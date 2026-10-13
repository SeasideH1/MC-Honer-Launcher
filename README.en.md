# MC Honer

English · [中文](README.md)

MC Honer is a Windows desktop launcher for Minecraft: Java Edition. It brings account management, isolated game instances, modpack downloads and updates into one interface. The project also implements a main service and a self-hostable distribution service for modpack maintainers, covering signed releases, access grants and server-reported playtime.

The project is under development. Its internal version is `0.1.0-alpha.1`. This repository publishes project information and images for users, developers and application reviewers. Source code, executables and deployment packages are not currently available here. This publication does not indicate Microsoft / Minecraft API approval or production acceptance.

![MC Honer project artwork](assets/honer-announcement.png)

*Announcement background used by the launcher. This is project artwork, not an in-game screenshot.*

## Current functionality

The launcher implements instance creation and import, per-instance settings, Java runtime management, game-file downloads and process launching. Modpack updates use signed manifests and file verification, with local configuration conflict handling and transaction recovery. Update recovery does not replace independent world backups.

Microsoft sign-in uses the device authorization flow. The launcher opens the system browser, and the user signs in on Microsoft's website; the launcher does not ask for the Microsoft account password. The implementation includes Microsoft, Xbox Live, XSTS and Minecraft Services authentication, plus Minecraft entitlement and player-profile retrieval. Live authorization with this project's application ID remains pending approval and subsequent testing.

The main service verifies Minecraft identity, provisions platform accounts, manages friends and invitations, issues distribution access grants and aggregates statistics. It does not use a separate platform password. Distribution services handle modpack descriptions, signed releases, file delivery and download limits. Trusted game servers report session events through a server-only adapter; local guest timers are kept separate from server-confirmed playtime.

OPL networking integration is implemented and has been checked with two nodes on one machine. Cross-network connectivity and player sign-in through a tunnel remain unverified. Executable plugin extensions, launcher self-updates and Linux / macOS releases have not been delivered. Room management, weapon loadouts and an SSH Editor are outside the current delivery scope.

## Interface preview

![MC Honer development build showing a local guest profile and empty statistics](assets/launcher-preview.png)

*Existing Windows desktop smoke-test capture of the development build's local guest page. It contains no verified online account or real player statistics. The interface is still being revised.*

## Implementation and deployment boundaries

| Component | Current implementation and responsibility |
| --- | --- |
| Windows client | Electron desktop window; a local Node.js core and SQLite manage instances and tasks. The UI accesses the core through a restricted set of IPC operations. |
| Main service | Node.js and PostgreSQL; identity verification, social features, directory, access grants and statistics. |
| Distribution service | Node.js with signed manifests, immutable content directories and a durable event queue; independently deployable by third parties. |
| Game-server adapter | Server-side Fabric component for admission and statistics; this integration requires no additional client mod. |

The development project requires Node.js 24 or later and uses Electron 44.7.0. The main service requires PostgreSQL. The Java version depends on the game instance; the current isolated test target is Minecraft `26.4 Snapshot 3`, Fabric `0.19.5` and Java `25.0.1`. These versions identify the implementation and test environment, not a compatibility guarantee for other combinations.

Maintainers supply service addresses, the Microsoft application ID and trust information through a distribution configuration. Players do not need to register an application. Windows user data defaults to `%APPDATA%\MC-Honer`, separate from the installation directory. Microsoft refresh tokens are kept in the local credential vault protected by Windows DPAPI. Platform sign-in sends a short-lived Minecraft token to the configured trusted main service for verification against official services; modpack distribution servers receive signed access grants only.

This public repository contains no application entry point, dependency manifest or service configuration. Cloning it does not provide a runnable or deployable application, so installation commands are not provided at this stage. Public packages and their deployment instructions will be supplied separately when ready for release.

## Verification scope and known limitations

Internal development records dated October 13, 2026 for `0.1.0-alpha.1` include Windows Electron and portable-package smoke tests, an isolated PostgreSQL 18.4 loopback instance, signed updates through a local distribution service, and an offline account reaching the main menu of the Minecraft / Fabric combination above and exiting normally. Local HTTP concurrent-download checks are not public-network capacity tests. These are development-environment records; internal test tools and raw logs are not included in this repository.

Live Microsoft authorization with this project's approved application, authenticated player admission to an online-mode server, a complete join-to-leave statistics session, cross-network OPL, public deployment and target-scale capacity remain unverified. The current candidate has no Windows code signature. No public production release or production service is provided by this project at this stage.

## Project and third-party information

MC Honer is an independent third-party project, not affiliated with or endorsed by Microsoft or Mojang. This repository distributes no Minecraft game files, third-party mods or player data. Publishing this overview does not grant access to the source code or a software redistribution licence. See [NOTICE.md](NOTICE.md) for provenance, dependencies and image information.
