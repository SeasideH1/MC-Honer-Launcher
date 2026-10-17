# 来源与第三方说明 / Provenance and third-party notices

## 中文

`assets/account-verification-alpha28-en.png` 来自 alpha.28 实际打包客户端的账号入口烟测；`assets/installer-alpha28-en.png` 来自该版本实际 WPF 安装器的预览渲染，使用示例安装目录，未执行安装。

alpha.28 安装包保留 Electron / Chromium 许可证、第三方声明及 OpenP2P 引擎的 MIT 许可证和修改来源记录。下文提及未发布依赖的段落描述此前仅公开介绍的阶段。

Git 仓库包含 MC Honer Launcher（MCHL）的公开文档与图片，GitHub Release 另行提供 Windows 预发行二进制程序。开发源码不公开，也未为本项目选择开源许可证。内部工程的 `LicenseRef-Private-Project` 是打包标识，不是标准开源许可证。第三方软件、商标与内容保留各自的许可和使用条件。

MC Honer Launcher 的部分启动器业务模块移植自项目维护者的 AiMatrixLauncher 工程，界面基于维护者提供的 MC Honer 原型。PCL / OPL 作为功能设计参考；未复制其 GUI 源码。

2026-10-13 记录的内部 Windows 候选包使用 Electron 44.7.0 及其 Chromium / Node.js 运行时，主服务使用 `pg` 8.23.1。其依赖和相应许可证不随本介绍仓库分发。后续分发程序包时须保留 Electron 的 `LICENSE`、`LICENSES.chromium.html` 及其他随包依赖声明。

同批内部候选包还使用基于 OpenP2P 3.25.11 的修改版引擎，沿用其上游 MIT 许可证。修改限制目标为明确允许的本机 Minecraft TCP 端口，并关闭自动全局防火墙修改。分发该引擎时须保留上游许可证与修改来源记录。该引擎及修改源码不包含在本仓库中。

Minecraft、Java、PostgreSQL、Fabric、第三方模组与游戏资源由各自权利人提供。本仓库不分发这些内容，不授予使用它们的额外权利，也不替代合法的游戏访问资格。

MCHL 不二次分发 Minecraft 游戏、原版代码或原版资源资产。整合包分发仅限自定义内容；第三方模组、材质包和光影包须按各自许可分发，并保留必要署名与声明。此规则不表示所有候选整合包已完成逐项许可审查。

README 中的 `assets/launcher-welcome-en.png`、`assets/launcher-home-en.png`、`assets/account-signin-en.png` 和 `assets/game-settings-en.png` 是维护者提供的启动选择、AiMatrix 主界面、账号登录和游戏设置截图。截图展示开发中的界面，不作为真实授权、游戏启动或跨平台兼容性验收的证据。

仓库保留的 `assets/aimatrix-download.png` 与 `assets/aimatrix-download-en.png` 是此前 `0.1.0-alpha.15` 打包客户端的实际中英文截图，显示 AiMatrix 游戏资源准备入口；`assets/installer-zh.png` 是该版本 Windows 安装向导的实际完成页面。这些截图不证明游戏已下载、启动或通过在线认证。

仓库保留的 `assets/honer-announcement.png` 是项目现有的 AI 生成公告背景；`assets/launcher-preview.png` 是此前开发工程的 Windows 桌面烟测截图，显示本机游客页面。两张历史图片均沿用现有工程资源，不代表游戏官方素材或正式发行界面。

## English

`assets/account-verification-alpha28-en.png` captures the actual packaged alpha.28 account-entry smoke test. `assets/installer-alpha28-en.png` is rendered by that version's WPF installer preview with an example destination; it does not document a completed installation.

The alpha.28 package retains Electron / Chromium licences, third-party notices and the OpenP2P engine MIT licence and modification provenance. Statements below about unpublished dependencies describe the earlier documentation-only stage.

The Git repository contains public MC Honer Launcher (MCHL) documentation and images. GitHub Releases separately provides Windows prerelease binaries. The development source remains private, and no open-source licence has been selected for the project. The internal `LicenseRef-Private-Project` value is a packaging identifier, not a standard open-source licence. Third-party software, trademarks and content retain their respective terms.

Some launcher modules were adapted from the maintainer's AiMatrixLauncher project. The interface is based on the supplied MC Honer prototype. PCL / OPL informed functional design; their GUI source was not copied.

The internal Windows candidate recorded on October 13, 2026 uses Electron 44.7.0 and its Chromium / Node.js runtime; the main service uses `pg` 8.23.1. Those dependencies and their licence files are not distributed in this overview repository. Any later application distribution must retain Electron's `LICENSE`, `LICENSES.chromium.html` and the applicable dependency notices.

That candidate also uses a modified OpenP2P 3.25.11 engine under its upstream MIT licence. Changes restrict destinations to explicitly allowed loopback Minecraft TCP ports and disable automatic global firewall changes. Distribution of that engine must retain its upstream licence and modification provenance. Neither the engine nor its modified source is included here.

Minecraft, Java, PostgreSQL, Fabric, third-party mods and game resources are supplied by their respective rights holders. This repository does not distribute them, grant additional rights to them or replace legitimate game access.

MCHL does not redistribute Minecraft, its vanilla code or its vanilla resource assets. Modpack distribution is limited to custom content. Third-party mods, resource packs and shader packs must be distributed under their respective licences with required attribution and notices. This policy does not establish that every candidate modpack has completed an asset-by-asset licence review.

The README images `assets/launcher-welcome-en.png`, `assets/launcher-home-en.png`, `assets/account-signin-en.png` and `assets/game-settings-en.png` were supplied by the maintainer. They show the start selection, AiMatrix home, account sign-in and game settings screens. They document an interface under development and do not establish successful live authentication, game launch or cross-platform compatibility.

The retained `assets/aimatrix-download.png` and `assets/aimatrix-download-en.png` are earlier Chinese and English captures of the packaged `0.1.0-alpha.15` client, showing the AiMatrix game preparation entry. `assets/installer-zh.png` shows the completion page of that version's Windows installer. These captures do not establish that the game was downloaded, launched or authenticated online.

The retained `assets/honer-announcement.png` is existing AI-generated project announcement artwork. `assets/launcher-preview.png` is an earlier Windows desktop smoke-test capture showing a local guest page. Both historical images reuse existing project assets; they do not represent official game artwork or a final release interface.
