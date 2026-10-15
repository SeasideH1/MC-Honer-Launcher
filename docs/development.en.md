# MC Honer Launcher development notes

[Back to the project overview](../README.en.md)

| Component | Current implementation and responsibility |
| --- | --- |
| Windows client | Electron desktop window; a local Node.js core and SQLite manage instances and tasks. The UI accesses the core through a restricted set of IPC operations. |
| Main service | Node.js and PostgreSQL; identity verification, social features, directory, access grants and statistics. |
| Distribution service | Node.js with signed manifests, immutable content directories and a durable event queue; independently deployable by third parties. |
| Game-server adapter | Server-side Fabric component for admission and statistics; this integration requires no additional client mod. |

The development project requires Node.js 24 or later and uses Electron 44.7.0. The main service requires PostgreSQL. The Java version depends on the game instance; the isolated test target recorded on October 13, 2026 was Minecraft `26.4 Snapshot 3`, Fabric `0.19.5` and Java `25.0.1`. These versions identify the inspected dependencies and historical test environment, not a compatibility guarantee for other combinations.

Maintainers supply service addresses, the Microsoft application ID and trust information through a distribution configuration. Players do not need to register an application. Windows user data defaults to `%APPDATA%\MC-Honer`, separate from the installation directory. Microsoft refresh tokens are kept in the local credential vault protected by Windows DPAPI. Platform sign-in sends a short-lived Minecraft token to the configured trusted main service for verification against official services; modpack distribution servers receive signed access grants only.

This public repository contains no application entry point, dependency manifest or service configuration. Cloning it does not provide a runnable or deployable MC Honer Launcher application, so installation commands are not provided at this stage. Public packages and their deployment instructions will be supplied separately when ready for release.

## Development records

Internal development records dated October 13, 2026 for `0.1.0-alpha.1` include Windows Electron and portable-package smoke tests, an isolated PostgreSQL 18.4 loopback instance, signed updates through a local distribution service, and an offline account reaching the main menu of the Minecraft / Fabric combination above and exiting normally. Local HTTP concurrent-download checks are not public-network capacity tests. These are development-environment records; internal test tools and raw logs are not included in this repository.

Those records also include an OPL connection test between two nodes on one machine, without cross-network coverage. That candidate had no Windows code signature. These historical results do not establish that later versions have passed live Microsoft authorization, authenticated server admission, complete player-session statistics or public-network capacity acceptance.

## Current client

In `0.1.0-alpha.15`, the window, tray, shortcuts and installer use MC Honer Launcher (MCHL). Language is selected in Settings. New profiles follow the system language; existing preferences are preserved. The application ID, executable filename and `%APPDATA%\MC-Honer` data directory retain compatibility. Account names, paths and remote publisher content are not automatically translated.

The regular client allows local offline identities. Offline launch requires a trusted remote's signed policy declaring a public modpack, allowing `offline` accounts and explicitly offering `offline-singleplayer` or `offline-opl`. Single-player rejects server addresses. OPL requires a running engine and allows only enabled local tunnels. Older policies allowing offline accounts without these modes do not automatically grant access. Private modpacks still require a verified game identity and valid access grants. Test access must not involve commercial payment conditions.

These checks cover launcher-issued launch and connection parameters. They do not prevent manual in-game actions or replace server-side online authentication. Microsoft sessions cannot fall back to tokenless offline sessions.

On October 15, 2026, 45 targeted tests passed on Windows with Node.js `24.19.0` and Electron `44.7.0`, covering language persistence, authentication, signed offline policies, remote policy migration and update verification. Both source and packaged clients passed actual-window checks for Settings language switching, persistence after reload and offline identity entry points. This round did not launch Minecraft or validate live Microsoft authorization, cross-network OPL or an upgrade over an existing installation.

The Microsoft application has not been approved for Minecraft Services access. Live authorization and server admission still require verification after access is granted. Before distributing a modpack, each third-party item's redistribution rights must also be checked, along with the exclusion of vanilla Minecraft code and resource assets.

Room management, weapon loadouts and an SSH Editor are outside the current development scope.
