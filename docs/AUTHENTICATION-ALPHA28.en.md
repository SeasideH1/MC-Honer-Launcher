# Authentication and launch controls in MC Honer Launcher 0.1.0-alpha.28

## Purpose and status

MC Honer Launcher (MCHL) is an independently developed Minecraft: Java Edition launcher for managing accounts, separate game instances and modpack updates. This document describes the alpha.28 implementation submitted for review. It does not establish approval by Mojang or Microsoft. The public Windows x64 installer is unsigned; macOS and Linux packages are not part of this release.

Alpha.28 replaces the earlier policy that allowed independently created offline identities. Game process creation now requires a Microsoft-linked Java identity verified against Minecraft Services, or an unexpired local record of that verification. A remote operator's modpack access grant, platform account or OPL connection cannot substitute for this check. Historical documentation about standalone offline identities describes previous versions only.

## Verification method

The client uses Microsoft's consumer device authorization flow, followed by Xbox Live, XSTS and Minecraft Services token exchange. Players enter their Microsoft credentials on Microsoft's pages; the launcher does not ask for their Microsoft password. The application must use its own registered and approved AppID. No third-party launcher's AppID is bundled as a substitute.

Before an online launch, the client queries `https://api.minecraftservices.com/entitlements/mcstore` and `https://api.minecraftservices.com/minecraft/profile` using the Minecraft access token. These requests target fixed HTTPS endpoints and do not follow redirects. The current implementation requires an entitlement named `game_minecraft` or `product_minecraft`, a valid Java profile name and a 32-character hexadecimal UUID matching the selected account. An empty or unrecognized entitlement list is rejected, even when a profile exists. Subscription response variants, including Game Pass, have not been validated live; this release does not promise support for variants outside these recognized responses.

The core performs the check after required installation work and before constructing the game process. Immediately before process creation, it rechecks the selected account, token, UUID, profile name and local verification expiry. This second check prevents an account change or expiry during server-admission work from reusing an earlier result. Both normal UI launches and direct core launch requests are subject to the identity check.

## Previously verified accounts without network access

In Settings → Accounts and launch, select Default game settings, enable **Use a verified account offline**, then save. The game files and Java runtime must already be available locally. This setting skips online token verification and automatic update checks; turn it off when online access is restored. Cached launch is also attempted if the online identity request fails with a network connection error. A modpack's separate policy and any required server admission still apply; these may require connectivity.

Successful official verification creates a record inside the existing encrypted credential vault. It binds the verified UUID and profile name to a SHA-256 digest of the Minecraft access token and records the verification time, last use and expiry. On Windows the vault uses authenticated encryption with a key protected by Windows DPAPI. Ordinary account-list metadata is insufficient to authorize launch.

The record expires at the earlier of the Minecraft token's expiry and 24 hours after verification. Offline use updates its last-use time without extending its validity. Missing, expired, inconsistent or backward-clock records are rejected. The same verified UUID, profile name and unexpired Minecraft token are passed to the game; the client does not generate a replacement identity or substitute a tokenless session.

When online verification returns an explicit rejection, missing entitlement, invalid profile, identity mismatch, throttling or another HTTP/API error, the client invalidates the local verification record and blocks launch. Only a network connection error may fall back to an existing valid record. An already invalidated record cannot be restored by enabling offline mode.

This bounded cache cannot detect an entitlement revoked while the client is disconnected. Its protection also does not establish resistance to an attacker controlling the user's operating-system account or modifying the executable. It is a local continuity mechanism, not a new entitlement issuer, and does not override server-side authentication.

## OPL and remote trust boundaries

OPL provides connectivity between endpoints. It neither creates a game identity nor verifies or grants a Minecraft entitlement. An active tunnel and a remote operator's permission cannot authorize an offline or third-party identity to launch the game. Remote signatures authenticate the publisher and the pack's policy; they are not evidence of game ownership.

Legacy `offline-singleplayer` and `offline-opl` policy identifiers remain readable for compatibility, but they are connection modes only and still require a verified Microsoft account. Old policies that allow only `offline` accounts no longer authorize launch. Operators must publish a compatible signed policy; the client does not silently rewrite it. Existing offline and third-party account records are retained locally but cannot be selected for launch. Their public creation endpoints are disabled.

The launcher does not change a game server's online-authentication setting. Server operators remain responsible for authenticating clients and enforcing their admission rules, including for connections transported through OPL. A successful local cached launch does not establish permission to join a server.

## Data handling and distribution

Microsoft refresh credentials remain in the client's local vault. Platform sign-in separately sends a short-lived Minecraft access token to the configured trusted main service, which verifies it against official endpoints before associating a platform identity with the Java UUID. Modpack distribution services receive scoped access grants rather than Microsoft refresh credentials. A platform grant cannot replace the client's game verification.

The launcher and distributed modpacks do not include vanilla Minecraft code, game binaries or resource assets. Modpacks are limited to custom content such as appropriately licensed mods, resource packs, shader packs and configuration. Vanilla files are obtained separately from official or authorized sources. Each third-party item's redistribution permission still requires review. MCHL does not sell accounts, game entitlements, subscriptions or test access; test access must not be tied to payments or donations.

The project is maintained by the individual developer [SeasideH1](https://github.com/SeasideH1). Contact: [qq1602770686@outlook.com](mailto:qq1602770686@outlook.com). Public application binaries include their required third-party notices. The private development repository is not published.

## Evidence and remaining validation

On October 17, 2026, Windows x64 with Node.js 24.19.0 ran 57 targeted tests: 56 passed and one PostgreSQL test was skipped because no isolated test database was configured. Tests covered Microsoft token handling, entitlement and profile rejection, cache expiry and binding, account changes, remote policy checks, OPL restrictions, update ordering, language settings and platform qualifications. Official-service responses were controlled fixtures, not live authorization results.

A process-boundary test used a compiled Windows test executable to observe whether the core created a child process. It confirmed a permitted cached launch and rejection before process creation when verification was absent, invalidated or associated with an unsupported identity. This executable was not Minecraft. A separate real local HTTP test confirmed that explicit offline mode uses an already saved signed policy without checking or downloading updates. The update-only test replaced game execution and did not itself prove authentication.

The package uses Electron 44.7.0. Packaged startup and language smoke results are recorded in the GitHub release notes. Build completion and UI smoke tests do not establish live Microsoft sign-in, successful Minecraft launch, cross-network OPL operation or authenticated server admission.

The distributed configuration currently has no approved Microsoft AppID configured, so a fresh installation cannot complete Microsoft sign-in or authorize game launch. Guest browsing and instance management remain available. The maintainer must configure the application's own approved AppID before a full live acceptance test. Changes to the separately deployed main service require an operator deployment; publication of this client does not update production servers.
