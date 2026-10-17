> NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.

![MC Honer Launcher start selection screen](assets/launcher-welcome-en.png?v=450368d)

# MC Honer Launcher (MCHL)

English · [中文](README.md)

![MC Honer Launcher — AiMatrix home screen](assets/launcher-home-en.png?v=450368d)

MC Honer Launcher is a Minecraft: Java Edition launcher under development, targeting Windows, macOS and Linux. It manages game accounts, separate game instances and modpack updates.
The client supports Simplified Chinese and English. Switch under Settings → Appearance → Interface language.

The GitHub repository owner, [SeasideH1](https://github.com/SeasideH1), is the individual developer responsible for this product.
Contact: [qq1602770686@outlook.com](mailto:qq1602770686@outlook.com).
The launcher is still in early development and testing. [GitHub Releases](https://github.com/SeasideH1/MC-Honer-Launcher/releases/tag/v0.1.0-alpha.28) provides a Windows x64 prerelease installer. The development source remains private. macOS and Linux remain development targets; this release includes no packages for them.

## Sign-in, distribution and server access

![alpha.28 Microsoft account verification entry](assets/account-verification-alpha28-en.png)

Account sign-in verifies a player's legitimate Minecraft identity and entitlement to the game. Players authorize access through Microsoft's official sign-in page. The client retrieves the Minecraft player profile, and the main service verifies the identity before creating a platform account without a separate password.
The authentication flow is implemented, but the application has not been approved for Minecraft Services access. The complete live sign-in and server admission flow remains unverified.

MCHL does not redistribute Minecraft. Modpack distribution contains only custom content, including mods, resource packs, shader packs and configuration files. It excludes vanilla Minecraft code, binaries and resource assets. The client obtains the game and vanilla resources separately from official or authorized sources.

The project contains no commercial paid content. Its operating rules allow players with a legitimate game entitlement to download the corresponding modpacks and join servers. Third-party remote servers connected to the platform may select a subset of players according to their testing plans. Test access must not involve commercial activity: it cannot be sold or tied to payments, donations, memberships, or purchases of other goods or services. Test players must also hold a legitimate game entitlement.

Starting with alpha.28, game launch requires a Microsoft account verified against Minecraft Services. A previously verified account may launch without network access while its local verification remains valid: no later than the Minecraft token's expiry and at most 24 hours after verification. Offline use does not renew the record. Missing entitlement, expired verification or an explicit official rejection blocks launch. Legacy offline and third-party account records are retained but cannot launch the game.

OPL provides connectivity only; it cannot establish or replace game entitlement. A remote operator's test-access grant cannot bypass verification. Servers remain responsible for independently authenticating players. See the [authentication review](docs/AUTHENTICATION-ALPHA28.en.md) for the checks and limitations.

## Installation and use

![alpha.28 Windows installer preview; no installation performed](assets/installer-alpha28-en.png)

1. Download `MC-Honer-0.1.0-alpha.28-x64-Setup.exe` from the [alpha.28 release](https://github.com/SeasideH1/MC-Honer-Launcher/releases/tag/v0.1.0-alpha.28) on Windows x64. This is an unsigned development prerelease.
2. Run the installer, choose a dedicated installation folder and interface language, then open the client. Settings provides language, instance and account controls.
3. The current package does not have an approved Microsoft AppID configured, so a fresh installation cannot complete sign-in or launch the game. Once the maintainer configures this application's approved AppID, players can authorize through Microsoft's pages, complete game verification, select the account for an instance and launch.

Users with a valid local verification and an already prepared game and Java runtime can select Default game settings under Settings → Accounts and launch, enable Use a verified account offline, and save. Disable it when back online. Private modpack access and server admission may still require connectivity.

The interface images below preserve earlier development screens. The account rules for alpha.28 are described on this page and in the authentication review.

## Features and interface

![MC Honer Launcher game settings page](assets/game-settings-en.png?v=450368d)

Each game instance keeps its own version, account selection and launch settings. The client supports creating and importing instances, managing Java runtimes, downloading game files and launching the game.
Modpack updates connect to the remote update server defined by the launcher platform server to update the game client automatically.

The main service manages platform accounts, friends, invitations and access grants. A separate distribution service publishes modpacks and serves downloads.

## Development status

The client uses Electron and Node.js, with SQLite for local data. The main service uses PostgreSQL.
The launcher runs separately from the game server.

The current public prerelease is `0.1.0-alpha.28`. See the [development notes](docs/development.en.md) for the versions, environments and scope of recorded tests. These records do not establish release readiness. See [NOTICE.md](NOTICE.md) for software provenance, artwork and third-party licences.
