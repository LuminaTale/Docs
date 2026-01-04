# 简介
**LuminaTale** 是一个基于 Rust 构建的现代高性能视觉小说（Visual Novel）引擎。

与传统的基于 Web 技术或 PyGame 的引擎不同，LuminaTale 采用了 **Skia** 作为 2D 渲染后端，并利用 **Vulkan** 进行硬件加速，旨在为创作者提供极致的性能表现和流畅的视觉体验。同时，它内置了专为 AVG 设计的 **Viviscript** 脚本语言，让剧本创作变得像写小说一样简单。

## 🌟 核心特性

- **高性能渲染架构**：
  基于 `lumina-skia-renderer`，利用 Skia 图形库和 Vulkan 后端，支持高分辨率矢量绘图、动态粒子效果和流畅的动画表现。

- **Viviscript 脚本语言**：
  专为视觉小说设计的领域特定语言（DSL）。语法简洁直观，支持角色定义、演出控制、分支选项和条件判断，极大降低了非程序员的创作门槛。

- **Lua 扩展系统**：
  内置 Lua 虚拟机，通过 `lua_glue` 层与 Rust 核心深度绑定。开发者可以使用 Lua 编写复杂的系统逻辑、自定义 Tween 动画生成器、甚至控制底层渲染参数。

- **双模渲染后端**：
  - **Skia GUI 模式**：全功能的图形界面，支持 Shader 特效和多媒体。
  - **TUI 终端模式**：支持在纯命令行环境下运行游戏，便于在低配设备或 SSH 环境下调试逻辑流程。

- **现代音频系统**：
  基于 `kira` 音频库，支持 BGM 无缝循环、音效多通道并发播放以及淡入淡出控制。

## 🏗️ 架构概览

LuminaTale 采用模块化的 Workspace 结构设计：

| 模块 | 说明 |
|------|------|
| **viviscript-core** | 编译器前端，负责将脚本解析为抽象语法树 (AST)。 |
| **lumina-core** | 引擎核心，包含虚拟机 (Executor)、资源管理和状态机。 |
| **lumina-skia-renderer** | 基于 Skia 的高性能渲染实现。 |
| **lumina-ui** | 独立的 UI 组件库 (Button, Panel, Slider 等)。 |
| **lumina-desktop** | 桌面端启动入口和配置管理。 |

> [!WARNING]
> 本项目仍处于极早期阶段, 本 Docs 文档以及 API 接口处于快速变动中!!!