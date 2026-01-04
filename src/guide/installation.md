# 安装与环境配置
LuminaTale 是基于 **Rust** 语言构建的，并使用 **Vulkan** 图形接口进行渲染。这意味着在运行引擎之前，我们需要准备好两样东西：**编译器**（把代码变成软件的工具）和 **开发环境**（让系统支持图形渲染的库）。

因为引擎目前仍然处在早期阶段，所以前这个部分会有些复杂，不过不用担心跟着这份说明一步一步的向下就好了。同时如果真的遇到了未提及的错误，自行去搜索引擎中搜索，大部分时间也是可以找到解决方法的。

---

## 第一步：安装 Rust 工具链

Rust 是编写本引擎的主要语言。

### 🪟 Windows 用户
1.  访问 [rustup.rs](https://rustup.rs/)。
2.  下载并运行 `rustup-init.exe`。
3.  **重要提示**：安装程序可能会提示你缺少 "C++ Build Tools"（Visual Studio 生成工具）。
    * **请务必安装它！** 它是编译底层依赖所必需的。
    * 在 Visual Studio Installer 中，勾选 **"使用 C++ 的桌面开发" (Desktop development with C++)** 进行安装。
4.  安装完成后，打开一个新的终端（PowerShell 或 CMD），输入 `cargo --version`，如果能看到版本号，说明安装成功。

### 🍎 macOS 用户
1.  打开终端（Terminal），输入以下命令并回车：
    ```bash
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```
2.  按照屏幕提示完成安装（通常直接回车即可）。
3.  你需要安装 Xcode 命令行工具（如果还没安装）：
    ```bash
    xcode-select --install
    ```

### 🐧 Linux 用户
1.  在终端运行安装脚本：
    ```bash
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```
2.  你需要安装基础的构建工具（gcc, make 等）。以 Ubuntu/Debian 为例：
    ```bash
    sudo apt update
    sudo apt install build-essential pkg-config libssl-dev
    ```

---

## 第二步：安装 Vulkan SDK
LuminaTale 使用 Skia 结合 Vulkan 进行高性能渲染。虽然显卡驱动通常包含运行库，但编译引擎需要完整的 SDK（开发包）。

### 🪟 Windows 用户
1.  访问 [LunarG Vulkan SDK 下载页面](https://vulkan.lunarg.com/sdk/home#windows)。
2.  下载最新的 **Installer** 并安装。
3.  安装过程中保持默认选项即可。安装完成后，建议重启电脑以确保环境变量生效。

### 🍎 macOS 用户
macOS 原生不支持 Vulkan（它使用 Metal），但我们可以通过 MoltenVK 来支持。
1.  访问 [LunarG Vulkan SDK for macOS](https://vulkan.lunarg.com/sdk/home#mac)。
2.  下载并安装 SDK。
3.  **或者**，如果你使用 Homebrew，可以运行：
    ```bash
    brew install molten-vk
    ```
    *注：大部分情况下，Rust 的图形库会自动处理 MoltenVK 的链接，但安装 SDK 是最保险的做法。*

### 🐧 Linux 用户
你需要安装 Vulkan 的加载器和开发头文件。
* **Ubuntu/Debian**:
    ```bash
    sudo apt install libvulkan-dev vulkan-tools
    ```
* **Arch Linux**:
    ```bash
    sudo pacman -S vulkan-devel
    ```
* 你可以在终端输入 `vulkaninfo` 来检查 Vulkan 是否配置正确。

---

## 第三步：获取 LuminaTale 源码

现在环境已经准备就绪，将引擎代码下载到本地。

1.  你需要安装 **Git**（如果没有的话）。
    * Windows: 下载 [Git for Windows](https://git-scm.com/)。
    * macOS/Linux: 通常系统自带，或通过包管理器安装。
2.  在终端中运行：
    ```bash
    git clone https://github.com/LuminaTale/LuminaTale.git
    cd LuminaTale
    ```

至此，所有的准备工作都完成了！接下来让我们运行它。