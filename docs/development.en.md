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

## Before a player-facing release

The project is named MC Honer Launcher, abbreviated MCHL. Chinese and English clients are in preparation; bilingual interface support is not yet complete. Historical screenshots and the existing data directory retain the previous name.

Offline identities are for development and testing only. The current code still exposes a UI and an API for creating them, so access cannot yet be described as closed to ordinary players. Before release, these entry points and their permissions must be isolated and tested to confirm that ordinary players cannot use development identities. Server test access must also require a legitimate game entitlement and must not involve commercial payment conditions.

The Microsoft application has not been approved for Minecraft Services access. Live authorization and server admission still require verification after access is granted. Before distributing a modpack, each third-party item's redistribution rights must also be checked, along with the exclusion of vanilla Minecraft code and resource assets.

Room management, weapon loadouts and an SSH Editor are outside the current development scope.
