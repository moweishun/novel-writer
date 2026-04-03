# novel-writer

全流程小说创作辅助技能 | Full-Stage Novel Writing Assistant

## 简介

`novel-writer` 是一个面向 OpenCode/OpenClaw AI 的全流程小说创作辅助技能，覆盖从项目初始化到稿件导出的完整工作流。支持跨会话记忆、内置质量控制、灵活设定顺序。

## 核心能力

| 阶段 | 功能 |
|------|------|
| **世界观设计** | 构建地理、历史、力量体系、社会规则 |
| **人物设定** | 设计主角/配角/反派，包含人物弧线和关系网络 |
| **势力设定** | 构建势力冲突框架、内部矛盾与外交关系 |
| **大纲规划** | 支持三幕、起承转合、英雄之旅等多种叙事结构 |
| **分卷大纲** | 为每卷每章制定详细规划（POV 人物、情节点、钩子） |
| **章节编写** | 全自动生成，内置质量检查 |
| **章节修改** | 根据反馈精确修改 |
| **稿件导出** | 合并为完整 Markdown 文件 |

## 特色

### 🔒 质量铁律

内置五大保障机制：

- **防注水** — 每个段落必须有信息量或情感推进，禁止无意义描写堆砌
- **防重复** — 每章必须有新增量，连续场景功能不重复
- **去 AI 味** — 禁用"此外、至关重要、深入探讨、格局、织锦"等典型 AI 词汇
- **设定一致性** — 人物行为/世界观规则/势力关系前后一致
- **情节推进** — 每 3 章小转折，每 10 章大转折

### 🎯 灵活起点

从任意设定环节开始：
- 先设计核心人物 → 根据人物背景补充世界观
- 先构建世界框架 → 再设计其中的人物
- 先设计势力冲突 → 再补充人物和世界观

### 💡 主动建议

不等用户问，主动发现：
- 设定之间的逻辑矛盾
- 人物行为与性格的不一致
- 情节推进的薄弱环节
- 可能的优化方向

### 🧠 跨会话记忆

所有设定和进度保存在项目目录下的 `.novel-memory/` 中：

```
.my-novel-project/
├── .novel-memory/          # 记忆系统
│   ├── meta.json           # 项目元信息 + 用户偏好
│   ├── progress.json       # 进度追踪
│   ├── index.json          # 轻量索引（章节摘要、伏笔状态）
│   ├── world.json          # 世界观设定
│   ├── characters.json     # 人物库
│   ├── factions.json       # 势力库
│   ├── outline.json        # 总大纲
│   ├── volumes/            # 分卷数据
│   ├── chapters/           # 章节数据（含正文）
│   ├── foreshadowing.json  # 伏笔追踪
│   ├── timeline.json       # 时间线
│   ├── relationships.json  # 人物关系
│   └── history.json        # 变更历史（支持回滚）
└── output/                 # 导出稿件
    ├── manuscript.md       # 完整稿件
    └── volumes/            # 按卷导出
```

纯 JSON 文件存储，打开项目后直接继续，无需重新告诉 AI 设定。

## 安装

将本技能目录放置到以下位置之一：

**本地项目（推荐）**：
```bash
# 在你的小说项目目录下创建
mkdir -p .opencode/skills/novel-writer
cp SKILL.md README.md prompts/ references/ templates/ \
   .opencode/skills/novel-writer/
```

**全局安装**：
```bash
# ~/.config/opencode/skills/novel-writer/SKILL.md
```

确保 `SKILL.md` 的 `name` 字段与目录名一致（`novel-writer`）。

## 使用

### 启动关键词

在 OpenCode 对话中提到以下任意关键词即可触发：

- "写小说"
- "创作故事"  
- "设计世界观"
- "写一章"
- "设计人物"
- "规划大纲"
- "使用 novel-writer 技能"

### 工作流

```
Phase 0: 项目初始化 → 创建项目、记录偏好
     ↓
Phase 1-3: 设定阶段（顺序灵活）
     ├── 世界观设计
     ├── 人物设计  
     └── 势力设计
     ↓
Phase 4: 总大纲设计
     ↓
Phase 5: 分卷大纲
     ↓
Phase 6: 章节编写（全自动 + 质量检查）
     ↓
Phase 7: 导出稿件
```

### 配合 humanizer-zh

如果已安装 `humanizer-zh` 技能，可以在章节编写后调用进行二次润色，进一步去除 AI 味。

## 技术栈

- **依赖**: `@opencode-ai/plugin` v1.3.13
- **存储**: 纯 JSON（`.novel-memory/`）
- **输出**: Markdown
- **语言**: TypeScript + Bun

## 项目结构

```
novel-writer/.opencode/
├── SKILL.md                          # 技能主文件
├── README.md                         # 本文件
├── prompts/                          # 阶段化提示模板
│   ├── project-init.md               # 项目初始化
│   ├── worldbuilding.md              # 世界观生成
│   ├── character-design.md           # 人物设计
│   ├── faction-design.md             # 势力设计
│   ├── outline-generation.md         # 大纲生成
│   ├── volume-outline.md             # 分卷大纲
│   ├── chapter-writing.md            # 章节编写
│   └── chapter-revision.md           # 章节修改
├── references/                       # 参考文档
│   ├── writing-standards.md          # 写作质量标准
│   ├── story-structures.md           # 叙事结构参考
│   └── scene-diagnosis.md            # 场景功能性诊断
└── templates/                        # JSON Schema 模板
    ├── world-schema.json
    ├── character-schema.json
    ├── faction-schema.json
    ├── outline-schema.json
    └── chapter-schema.json
```

## 许可证

Apache License 2.0

---

**开始创作你的小说吧！📖**

在对话中说："使用 novel-writer，帮我写一部玄幻小说"即可启动。
