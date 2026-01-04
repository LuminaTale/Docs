# 配置文件详解

当引擎首次运行时，会在根目录自动生成一个 `config.toml` 文件。你可以通过修改它来调整游戏的分辨率、音量 defaults 等设置。

以下是默认配置文件的各个部分说明：

## `[system]` (系统设置)

控制引擎的基础路径和日志行为。

```toml
[system]
assets_path = "lumina-desktop/assets/"
script_path = "lumina-desktop/game/"
save_path = "lumina-desktop/saves/"
log_path = "lumina-desktop/logs/"
log_level = "debug"
```

## `[window]` (窗口设置)

控制游戏窗口的表现。

```toml
[window]
title = "LuminaTale"      # 游戏窗口标题
width = 1280              # 窗口宽度
height = 720              # 窗口高度
resizable = true          # 是否允许玩家拖拽改变窗口大小
vsync = true              # 是否开启垂直同步 (防止画面撕裂，锁定帧率)
```

## `[audio]` (音频设置)
```toml
[audio]
master_volume = 1.0       # 主音量 (0.0 ~ 1.0)
music_volume = 0.7        # 背景音乐音量
voice_volume = 0.8        # 语音音量
sound_volume = 0.8        # 音效音量
music_loop = true         # 音乐是否默认循环
fade_in_sec = 0.2         # 默认淡入时间 (秒)
fade_out_sec = 0.2        # 默认淡出时间 (秒)
voice_link_char = "_"     # 语音文件命名连接符 (如: alice_001.mp3)
```

## `[graphics]` (窗口设置)
```toml
[graphics]
default_transition = "dissolve" # 默认使用的转场效果名称
preload_ahead = 20              # 预加载步数 (为了流畅，提前加载后20句脚本的资源)
scene_zindex = 0                # 背景图层层级
sprite_zindex = 10              # 立绘图层层级
```

修改完 `config.toml` 后，重启游戏即可生效。