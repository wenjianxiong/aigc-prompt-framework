# 🎬 AIGC 影视提示词操作系统 v1.0

> **一句话定位**：为 AI 短剧、漫剧、电影短篇和实验影像提供生产级的可加载提示词框架。不是模板堆，是操作系统。

## 三层架构

```
🎬 类型模板（一行启动）→  短剧 / 漫剧 / 电影短篇 / 广告 / 实验
        ↓ 调用
🔧 生产管线（分阶段 Skill）→  剧本审核 → 分镜 → 角色 → 场景 → Seedance → 后期
        ↓ 注入
🧱 风格引擎（底层参数库）→  光影方案 / 镜头规格 / 质感描述 / 色彩板
```

## 快速启动

1. **只想要一条 Seedance 提示词** → 打开 `engine/styles/` 选风格，复制参数块
2. **想把剧本变成视频** → 打开 `chains/full-short-drama.chain`，跟随 Prompt Chain
3. **想做角色设定图** → 打开 `pipeline/03-character-design.md`，复制 System Prompt
4. **不知道怎么定价** → 打开 `knowledge/cost-guide.md`

## 目录结构

```
prompt-framework/
├── README.md                  ← 你在这里
├── index.json                 ← 结构化索引（机器可读）
│
├── engine/                    # Layer 1: 风格引擎
│   ├── styles/                # 风格预设（18种真人 + 10种动画 + 实验）
│   ├── lighting/              # 光影方案（12种）
│   ├── lenses/                # 镜头规格（7种）
│   └── textures/              # 质感描述（皮肤/金属/布料/自然环境）
│
├── pipeline/                  # Layer 2: 生产管线
│   ├── 01-script-review.md    # 剧本审核
│   ├── 02-script-to-storyboard.md  # 剧本→分镜
│   ├── 03-character-design.md # 角色设定（三视图）
│   ├── 04-scene-design.md     # 场景概念图
│   ├── 05-prop-design.md      # 道具特写
│   ├── 06-seedance-prompt.md  # Seedance 提示词组装
│   ├── 07-multi-shot-narrative.md  # 多镜头叙事
│   └── 08-post-production.md  # 后期合成
│
├── templates/                 # Layer 3: 一键模板
│   ├── short-drama.prompt
│   ├── manga-drama.prompt
│   ├── film-short.prompt
│   ├── ad-spot.prompt
│   └── experimental.prompt
│
├── knowledge/                 # 知识库
│   ├── seedance-guide.md
│   ├── cost-guide.md
│   ├── genre-guide.md
│   └── case-studies/
│
├── chains/                    # 端到端 Prompt Chain
│   ├── full-short-drama.chain
│   ├── full-manga.chain
│   └── full-film.chain
│
└── tools/                     # 辅助工具
    └── converters/
```

## 使用方式

### 在 OpenClaw 中使用
直接把任意 `.md` Skill 文件复制为 System Prompt，输入你的剧本即可。

### 在即梦/Seedance 中使用
从 `engine/` 中选取风格参数块，按 `pipeline/06-seedance-prompt.md` 的公式组装提示词。

### 跨 LLM 使用
所有 Skill 文件使用自然语言编写，不依赖特定模型格式。已在 DeepSeek V4 / ChatGPT / Gemini / 豆包 测试兼容。

## 设计原则

- **可加载**：每个文件可以直接作为 System Prompt 或上下文注入
- **可组合**：风格参数 + 管线 Skill + 类型模板可任意拼装
- **可迭代**：版本号清晰，每次变更留记录
- **跨模型**：自然语言编写，不绑定特定 LLM
- **实战导向**：所有模板和案例来自真实项目产出

## 版本

- v1.0 — 2026-05-20 — 初始框架，小赵构建
