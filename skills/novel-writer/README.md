# Novel-Writer: 全流程小说创作辅助技能

## 简介

Novel-Writer 是一个面向 opencode和openclaw 的全流程小说创作辅助技能，覆盖从项目初始化到稿件导出的完整工作流。

## 核心能力

- **世界观设计** — 构建地理、历史、力量体系、社会规则
- **人物设定** — 设计主角、配角、反派，包含人物弧线和关系网络
- **势力设定** — 构建势力冲突框架，内部矛盾与外交关系
- **大纲规划** — 支持三幕、起承转合、英雄之旅等多种叙事结构
- **分卷大纲** — 为每卷每章制定详细规划
- **章节编写** — 全自动生成，内置质量检查
- **章节修改** — 根据反馈精确修改
- **稿件导出** — 合并为完整 Markdown 文件

## 特色

### 质量铁律

内置防注水、防重复、去 AI 味、设定一致性、情节推进五大质量保障机制。

### 灵活起点

设定阶段顺序灵活，可以从世界观开始，也可以从人物或势力开始。

### 主动建议

不等用户问，主动发现设定矛盾、情节薄弱环节，提出优化建议。

### 跨会话记忆

所有设定和进度保存在项目目录下的 `.novel-memory/` 中，跨会话无缝继续。

## 安装

将本技能目录放置到以下位置之一：

- **项目本地**：`.opencode/skills/novel-writer/SKILL.md`
- **全局**：`~/.config/opencode/skills/novel-writer/SKILL.md`

确保 `SKILL.md` 的 `name` 字段与目录名一致（`novel-writer`）。

## 使用

### 启动

在 opencode 对话中提到以下关键词即可触发：

- "写小说"
- "创作故事"
- "设计世界观"
- "写一章"
- "设计人物"
- "规划大纲"

或直接说："使用 novel-writer 技能"

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
Phase 5: 分卷细纲
    ↓
Phase 6: 章节编写（全自动）
    ↓
Phase 7: 导出稿件
```

### 项目目录结构

使用技能后，你的小说项目目录将包含：

```
my-novel/
├── .novel-memory/          # 记忆系统（设定、进度、伏笔等）
│   ├── meta.json
│   ├── progress.json
│   ├── index.json
│   ├── world.json
│   ├── characters.json
│   ├── factions.json
│   ├── outline.json
│   ├── volumes/
│   ├── chapters/
│   ├── foreshadowing.json
│   ├── timeline.json
│   ├── relationships.json
│   └── history.json
└── output/                 # 导出稿件
    ├── manuscript.md
    └── volumes/
```

## 记忆系统

### 存储技术

纯 JSON 文件，存放在项目目录下的 `.novel-memory/` 中。

### 存储内容

- 所有设定（世界观、人物、势力、大纲）
- 章节正文和元数据
- 伏笔追踪（埋了什么、在哪、是否回收）
- 时间线（事件先后顺序）
- 人物关系变化
- 进度追踪
- 变更历史（支持回滚）

### 跨会话

打开项目后直接继续，不需要重新告诉 AI 设定。

## 文件说明

```
.opencode/skills/novel-writer/
├── SKILL.md                          # 技能主文件
├── README.md                         # 本文件
├── prompts/                          # 阶段化提示模板
│   ├── project-init.md               # 项目初始化
│   ├── worldbuilding.md              # 世界观生成
│   ├── character-design.md           # 人物设计
│   ├── faction-design.md             # 势力设计
│   ├── outline-generation.md         # 大纲生成
│   ├── volume-outline.md             # 分卷细纲
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

## 与 humanizer-zh 配合

如果已安装 `humanizer-zh` 技能，可以在章节编写后调用进行二次润色，进一步去除 AI 味。

## 许可证

MIT
