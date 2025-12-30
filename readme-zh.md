LÖVE 是一个*很棒*的框架，你可以用它来用 Lua 制作 2D 游戏。它是免费的、开源的，并且可以在 Windows、macOS、Linux、Android 和 iOS 上运行。

[![构建状态: Github CI](https://github.com/love2d/love/workflows/continuous-integration/badge.svg)](https://github.com/love2d/love/actions?query=workflow%3Acontinuous-integration)

文档
---

我们使用我们的 [wiki][wiki] 来提供文档。
如果你需要进一步的帮助，请随时在我们的 [论坛][forums]、[Discord 服务器][discord] 或我们的 [subreddit][subreddit] 上提问。

仓库
---

我们使用 'main' 分支来开发下一个主要版本，因此不应将其视为稳定版本。

还有当前发布的主要版本的分支，这些分支可能包含针对该主要版本内即将发布的补丁版本的修复和更改。

我们标记了所有发布版本（自从我们开始使用 mercurial 和 git 以来），并且有可供下载的二进制文件。

实验性更改有时会在单独的 [love-experiments][love-experiments] 仓库中开发。

构建
---

发布版本的文件在 GitHub 的 [releases][releases] 部分。[网站][site] 包含最新版本的文件链接和其他平台内容。

还有不稳定/每日构建版本：

- 某些平台的构建版本在每次提交后自动创建，并通过 GitHub 的 CI 界面提供。
- 对于 ubuntu linux，它们在 [ppa:bartbes/love-unstable][unstableppa]
- 对于 arch linux，AUR 中有 [love-git][aur]。

测试套件
--------

`testing/` 中的测试套件覆盖了所有 LÖVE API，并以开发者使用它们的方式进行测试。你可以从任何 [action][workflows] 查看当前的测试覆盖率。
你可以像运行普通 LÖVE 项目一样在本地运行套件，例如：
`love testing`

有关更多信息，请参阅 testing 文件夹中的 [readme][testsuite]。

贡献
----

贡献的最佳方式是通过问题跟踪器和官方 Discord 服务器或 IRC 频道。

对于代码贡献，欢迎提交拉取请求和补丁。请务必阅读 [源代码风格指南][codestyle]。
更改和新功能通常在提交拉取请求之前在问题跟踪器、Discord 或论坛上讨论。

编译
-----

### Windows
按照 [megasource][megasource] 仓库页面上的说明操作。

### *nix
由于不允许在源代码树内构建，因此需要在单独的构建目录中生成 Makefile。在此示例中，使用名为 `build` 的文件夹：

	$ cmake -B build -S. --install-prefix $PWD/prefix # 这将创建目录 `build/`。
	$ cmake --build build --target install -j$(nproc) # 这将使用所有核心进行构建，并将文件放在 `prefix/` 中。

> [!NOTE]  
> CMake 3.15 及更早版本不支持 `--install-prefix`。在这种情况下，请改用 `-DCMAKE_INSTALL_PREFIX=`。

### macOS
下载或克隆 [此仓库][dependencies-apple]，并将 `macOS/Frameworks` 子文件夹复制、移动或符号链接到 love 的 `platform/xcode/macosx` 文件夹中，将 `shared` 子文件夹复制、移动或符号链接到 love 的 `platform/xcode` 文件夹中。

然后使用位于 `platform/xcode/love.xcodeproj` 的 Xcode 项目来构建 `love-macosx` 目标。

### iOS
为 iOS 构建需要 macOS 和 Xcode。

从 [发布页面][dependencies-ios] 下载与正在使用的 LÖVE 版本对应的 `love-apple-dependencies` zip 文件，
解压缩它，并将 `iOS/libraries` 子文件夹放入 love 的 `platform/xcode/ios` 文件夹中，将 `shared` 子文件夹放入 love 的 `platform/xcode` 文件夹中。

或者，下载或克隆 [此仓库][dependencies-apple]，并将 `iOS/libraries` 子文件夹复制、移动或符号链接到 love 的 `platform/xcode/ios` 文件夹中，将 `shared` 子文件夹复制、移动或符号链接到 love 的 `platform/xcode` 文件夹中。

然后使用位于 `platform/xcode/love.xcodeproj` 的 Xcode 项目来构建 `love-ios` 目标。

有关更多信息，请参阅 `readme-iOS.rtf`。

### Android
访问 [Android 构建仓库][android-repository] 以获取构建说明。

依赖项
-------

- SDL3
- OpenGL 3.3+ / OpenGL ES 3.0+ / Vulkan / Metal
- OpenAL
- Lua / LuaJIT / LLVM-lua
- FreeType
- harfbuzz
- ModPlug
- Vorbisfile
- Theora

[site]: https://love2d.org
[wiki]: https://love2d.org/wiki
[forums]: https://love2d.org/forums
[discord]: https://discord.gg/rhUets9
[subreddit]: https://www.reddit.com/r/love2d
[dependencies-apple]: https://github.com/love2d/love-apple-dependencies
[dependencies-ios]: https://github.com/love2d/love/releases
[megasource]: https://github.com/love2d/megasource
[unstableppa]: https://launchpad.net/~bartbes/+archive/love-unstable
[aur]: https://aur.archlinux.org/packages/love-git
[love-experiments]: https://github.com/slime73/love-experiments
[codestyle]: https://love2d.org/wiki/Code_Style
[android-repository]: https://github.com/love2d/love-android
[releases]: https://github.com/love2d/love/releases
[testsuite]: https://github.com/love2d/love/tree/main/testing
[workflows]: https://github.com/love2d/love/actions/workflows/main.yml?query=branch%3Amain
