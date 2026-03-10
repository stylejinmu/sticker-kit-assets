# sticker-kit-assets

> 微信表情包合辑**配套素材**生成工具（Manus Skill）——专注于合辑文案与配套图片素材，不含表情图本身的生成。

## 简介

`sticker-kit-assets` 是一个面向 [Manus AI](https://manus.im) 的 Skill，帮助创作者快速生成微信表情包开放平台所需的全套**配套素材**，严格遵循官方尺寸、格式与设计规范。

本 Skill 基于 [sticker-kit](https://github.com/stylejinmu/sticker-kit) 衍生而来，去除了表情图生成部分，专注于以下内容：

- **合辑文案**：合辑名称、合辑介绍、赞赏引导语、每张表情的含义词
- **配套图片素材**：横幅图、封面图、图标、赞赏引导图、赞赏致谢图

## 素材规范

| 素材类型 | 格式 | 尺寸 (px) | 体积限制 | 背景要求 |
| :--- | :--- | :--- | :--- | :--- |
| 横幅图 | PNG | 750 × 400 | < 500 KB | **彩色不透明**，禁止透明/白色背景 |
| 封面图 | PNG | 240 × 240 | < 500 KB | 透明背景 |
| 图标 | PNG | 50 × 50 | < 100 KB | 透明背景 |
| 赞赏引导图 | GIF/PNG | 750 × 560 | < 500 KB | **彩色不透明**，禁止透明/白色背景 |
| 赞赏致谢图 | GIF/PNG | 750 × 750 | < 500 KB | **彩色不透明**，禁止透明/白色背景 |

## 文件结构

```
sticker-kit-assets/
├── SKILL.md                  # Manus Skill 主文件（工作流、规范、提示词指引）
└── scripts/
    └── process_sticker.py    # 图片自动化处理脚本（尺寸调整、体积压缩）
```

## 脚本用法

`process_sticker.py` 支持静态图与动态 GIF 的批量处理，自动完成缩放与体积压缩。

```bash
# 参数顺序：input output width height format max_kb [transparent] [is_animated] [loop_gif]

# 封面图（透明背景）
python3 scripts/process_sticker.py input.png cover.png 240 240 PNG 500

# 图标（透明背景）
python3 scripts/process_sticker.py head.png icon.png 50 50 PNG 100

# 横幅图（彩色不透明背景）
python3 scripts/process_sticker.py banner_src.png banner.png 750 400 PNG 500 False

# 赞赏引导图（彩色不透明背景）
python3 scripts/process_sticker.py guide_src.png guide.png 750 560 PNG 500 False

# 赞赏致谢图（彩色不透明背景）
python3 scripts/process_sticker.py thanks_src.png thanks.png 750 750 PNG 500 False
```

| 参数 | 默认值 | 说明 |
| :--- | :--- | :--- |
| `transparent` | `True` | 是否使用透明背景；横幅图、赞赏图须设为 `False` |
| `is_animated` | `False` | 是否处理动态 GIF |
| `loop_gif` | `False` | GIF 是否循环播放（仅 `is_animated=True` 时有效） |

## 如何在 Manus 中使用

将本仓库作为 Skill 添加到 Manus 后，在对话中描述你的表情包主题，Manus 将自动：

1. 生成合辑名称、介绍、赞赏引导语及每张表情的含义词
2. 调用脚本处理你提供的图片素材，输出符合规范的横幅图、封面图、图标及赞赏图
3. 按设计自检清单逐项核查，确保颜色鲜明、主体突出、文字清晰可见

## 相关项目

- [sticker-kit](https://github.com/stylejinmu/sticker-kit)：完整版表情包合辑素材生成工具，包含表情图生成

## License

MIT
