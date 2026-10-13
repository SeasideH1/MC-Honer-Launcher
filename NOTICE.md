# 来源与第三方说明 / Provenance and third-party notices

## 中文

本仓库仅包含 MC Honer 的公开介绍与图片，未发布软件源码或二进制程序，也未为本项目选择开源许可证。内部工程的 `LicenseRef-Private-Project` 是打包标识，不是标准开源许可证。第三方软件、商标与内容保留各自的许可和使用条件。

MC Honer 的部分启动器业务模块移植自项目维护者的 AiMatrixLauncher 工程，界面基于维护者提供的 MC Honer 原型。PCL / OPL 作为功能设计参考；未复制其 GUI 源码。

内部 Windows 候选包使用 Electron 44.7.0 及其 Chromium / Node.js 运行时，主服务使用 `pg` 8.23.1。其依赖和相应许可证不随本介绍仓库分发。后续分发程序包时须保留 Electron 的 `LICENSE`、`LICENSES.chromium.html` 及其他随包依赖声明。

内部候选包还使用基于 OpenP2P 3.25.11 的修改版引擎，沿用其上游 MIT 许可证。修改限制目标为明确允许的本机 Minecraft TCP 端口，并关闭自动全局防火墙修改。分发该引擎时须保留上游许可证与修改来源记录。该引擎及修改源码不包含在本仓库中。

Minecraft、Java、PostgreSQL、Fabric、第三方模组与游戏资源由各自权利人提供。本仓库不分发这些内容，不授予使用它们的额外权利，也不替代合法的游戏访问资格。

`assets/honer-announcement.png` 是项目现有的 AI 生成公告背景，作为介绍素材展示；`assets/launcher-preview.png` 是开发工程的 Windows 桌面烟测截图，显示本机游客页面。两张图片均沿用现有工程资源，不代表游戏官方素材、正式发行界面或已通过在线认证。

## English

This repository contains only public project information and images. It publishes no application source or binaries, and no open-source licence has been selected for the project. The internal `LicenseRef-Private-Project` value is a packaging identifier, not a standard open-source licence. Third-party software, trademarks and content retain their respective terms.

Some launcher modules were adapted from the maintainer's AiMatrixLauncher project. The interface is based on the supplied MC Honer prototype. PCL / OPL informed functional design; their GUI source was not copied.

The internal Windows candidate uses Electron 44.7.0 and its Chromium / Node.js runtime; the main service uses `pg` 8.23.1. Those dependencies and their licence files are not distributed in this overview repository. Any later application distribution must retain Electron's `LICENSE`, `LICENSES.chromium.html` and the applicable dependency notices.

The internal candidate also uses a modified OpenP2P 3.25.11 engine under its upstream MIT licence. Changes restrict destinations to explicitly allowed loopback Minecraft TCP ports and disable automatic global firewall changes. Distribution of that engine must retain its upstream licence and modification provenance. Neither the engine nor its modified source is included here.

Minecraft, Java, PostgreSQL, Fabric, third-party mods and game resources are supplied by their respective rights holders. This repository does not distribute them, grant additional rights to them or replace legitimate game access.

`assets/honer-announcement.png` is existing AI-generated project announcement artwork. `assets/launcher-preview.png` is a Windows desktop smoke-test capture from the development project showing a local guest page. Both images reuse existing project assets; they do not represent official game artwork, a final release interface or successful online authentication.
