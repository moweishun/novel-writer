# 项目初始化提示模板

## 目标

创建新的小说项目，收集用户偏好，初始化记忆系统。

## 执行步骤

### 1. 收集基本信息

询问用户以下内容（可省略任意项）：

- **小说标题**（可暂定）
- **题材/类型**：玄幻、科幻、历史、都市、仙侠、悬疑、言情、奇幻等
- **整体基调**：黑暗、轻松、史诗、写实、浪漫、荒诞等
- **目标总字数**：如 50 万字、100 万字
- **单章字数范围**：如 3000-5000 字

### 2. 收集风格偏好

- **叙事视角**：第三人称限知、第三人称全知、第一人称、多视角切换
- **叙事节奏**：慢热铺垫、中等偏快、快节奏、张弛有度
- **对话比例**：偏少（重描写）、适中、偏多（重对话）
- **文风参考**：是否有喜欢的作家或作品作为风格参考

### 3. 收集禁忌和要求

- **禁忌元素**：绝对不想写的内容（如系统流、穿越、后宫等）
- **必需要素**：一定要包含的元素（如群像、权谋、成长线等）
- **特殊要求**：其他用户特别在意的点

### 4. 初始化记忆系统

创建 `.novel-memory/` 目录及所有必要文件：

```
meta.json
progress.json
index.json
world.json
characters.json
factions.json
outline.json
foreshadowing.json
foreshadowing-history.json
timeline.json
relationships.json
relationships-history.json
history.json
volumes/ (空目录)
chapters/ (空目录)
history-archive/ (空目录)
```

### 5. 填充 meta.json

```json
{
  "project_id": "proj_{日期}_{序号}",
  "title": "{用户提供的标题}",
  "genre": "{题材}",
  "tone": "{基调}",
  "target_word_count": {目标字数},
  "chapter_word_range": [{最小字数}, {最大字数}],
  "created_at": "{ISO时间}",
  "updated_at": "{ISO时间}",
  "current_phase": "initialization",
  "user_preferences": {
    "narrative_style": "{叙事视角}",
    "pacing": "{叙事节奏}",
    "dialogue_ratio": "{对话比例}",
    "style_reference": "{文风参考}",
    "forbidden_tropes": ["{禁忌1}", "{禁忌2}"],
    "required_elements": ["{要素1}", "{要素2}"],
    "special_requirements": "{特殊要求}"
  }
}
```

### 6. 填充 progress.json

```json
{
  "current_phase": "initialization",
  "completed_phases": [],
  "current_volume": null,
  "current_chapter": null,
  "total_chapters_planned": null,
  "total_chapters_written": 0,
  "total_word_count": 0,
  "last_written_at": null
}
```

### 7. 填充 index.json

```json
{
  "chapters": [],
  "active_foreshadowing": [],
  "characters_status": [],
  "last_updated": "{ISO时间}"
}
```

### 8. 其他文件初始化为空结构

**world.json**:
```json
{
  "world_id": null,
  "name": null,
  "summary": null,
  "description": null,
  "era": null,
  "geography": { "regions": [], "key_locations": [] },
  "power_system": { "type": null, "rules": [], "limitations": [], "levels": [] },
  "history": { "timeline": [], "major_events": [] },
  "rules": { "physical": [], "social": [], "taboos": [] },
  "tone_keywords": [],
  "locked": false
}
```

**characters.json**:
```json
{ "characters": [] }
```

**factions.json**:
```json
{ "factions": [] }
```

**outline.json**:
```json
{
  "structure_type": null,
  "acts": [],
  "main_plot": null,
  "subplots": [],
  "themes": [],
  "core_conflict": null
}
```

**foreshadowing.json**:
```json
{ "foreshadowing": [] }
```

**foreshadowing-history.json**:
```json
{ "foreshadowing": [] }
```

**timeline.json**:
```json
{ "events": [] }
```

**relationships.json**:
```json
{ "relationships": [] }
```

**relationships-history.json**:
```json
{ "relationships": [] }
```

**history.json**:
```json
{ "history": [] }
```

### 9. 确认初始化完成

向用户展示项目概况：
- 项目名称、题材、基调
- 目标字数、章节字数范围
- 已记录的偏好和禁忌
- 下一步：开始设定阶段（世界观/人物/势力，用户自选起点）
