# 快速开始

环境配置完成后，我们来创建你的第一个游戏场景。

## 1. 清理/创建工作区

进入你刚下载的 `LuminaTale` 目录。虽然自带了一些示例，但我们建议从头开始。
请确保根目录下存在以下两个文件夹（如果没有请手动创建）：

* `game/`：我们将在这里写剧本，这里应该有一些以 **.lua** 结尾的文件，**请不要删除它们！！！** 后缀为 **.vivi** 的可以删掉。
* `assets/`：我们将在这里放图片和音乐。

请随便找一张你喜欢的图片命名为`bg_demo.png`，找一张人物图片命名为 `ch1.png`（这个的分辨率请不要太大，引擎目前对于角色大小处理还存在问题），然后放入 `assets/` 文件夹中。

## 2. 编写脚本

在 `game/` 文件夹内，新建一个文本文件，命名为 `start.vivi`（注意后缀是 `.vivi`）。
用你喜欢的文本编辑器（如 VS Code, Notepad++）打开它，粘贴以下代码：

```viviscript
-- 定义一个角色
character ch1 name="爱丽丝" image_tag="ch1"

-- 游戏的主入口标签，引擎启动后会自动寻找名为 'init' 的标签
label init

    -- 切换背景 (对应 assets/bg_demo.png)
    -- with fade_in 表示使用淡入效果
    scene bg demo with fade_in

    : (这是一段旁白) 这是一个风和日丽的下午。

    -- 显示角色立绘，位置在屏幕中间 (center)
    show ch1 at center

    -- 角色说话
    ch1: "你好，创造者！终于见到你了。"
    ch1: "这是我们的第一个场景。"

    -- 给玩家一个选择
    choice "你觉得怎么样？"
        "非常简单":
            ch1: "太棒了！Viviscript 的设计初衷就是简单易用。"
        "有点复杂":
            ch1: "别担心，查看文档，你会慢慢熟悉的。"
    enco

    : 演示结束。

    -- 这是一个跳转标签，意味着它将会跳转到标签名为 "stop" 的部分并执行
    jump stop
enlb

label stop
: 演示结束。
enlb
```

## 3. 启动引擎
回到项目根目录的终端，输入以下命令启动：

```bash
cargo run -p lumina-desktop
```

## （4.修改配置文件）
找到根目录下新生成的 `config.toml`， 并将`[system]`这节换成以下内容
```toml
[system]
assets_path = "lumina-desktop/assets/"
script_path = "lumina-desktop/game/"
save_path = "lumina-desktop/saves/"
log_path = "lumina-desktop/logs/"
log_level = "info"
```


发生了什么？
1. Cargo（Rust 的包管理器）会开始下载依赖并编译引擎。第一次运行可能会花费几分钟，请耐心等待（主要是在编译 Skia 图形库）。这一步经常会出现网络问题，所以请保证你能正常访问绝大多数的网站。
2. 编译完成后，一个名为 "LuminaTale" 的窗口将会弹出。
3. 引擎会自动读取 `config.toml`（如果不存在会自动生成在根目录下），然后加载 game/ 下的所有脚本。
4. 由于目前引擎尚处于开发过程，我们需要修改 `config.toml` 来让它正确指向我们的内容。
5. 你应该能看到你设置的背景、立绘和对话内容。

恭喜！你已经成功运行了你的第一个 LuminaTale 游戏。