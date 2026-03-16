# PM + OpenSpec 完美结合工作流

> 用 pm-skills 想清楚"做什么"，用 OpenSpec 管好"怎么做"

---

## 核心概念

| 工具 | 定位 | 功能 |
|------|------|------|
| **pm-skills** | 产品思考框架 | 发现、策略、规划 |
| **OpenSpec** | 开发流程管理 | 提案、规格、设计、任务 |

---

## 完整工作流

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           产品开发全生命周期                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────┐ │
│  │ 发现阶段  │ → │ 策略阶段  │ → │ 规划阶段  │ → │ 开发阶段  │ → │ 发布 │ │
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘    └──────┘ │
│       │              │              │              │              │        │
│       ↓              ↓              ↓              ↓              ↓        │
│  pm-skills      pm-skills      pm-skills      OpenSpec       pm-skills    │
│  /discover     /strategy      /write-prd    /archive       /plan-launch  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 阶段详解

### 阶段 1: 发现 (Discovery)

**目标**: 验证想法是否值得做

**使用 pm-skills**:
```
/discover
```

自动执行:
1. brainstorm-ideas - 头脑风暴
2. identify-assumptions - 识别假设
3. prioritize-assumptions - 优先级排序
4. brainstorm-experiments - 规划实验

**产出**: 发现报告

---

### 阶段 2: 策略 (Strategy)

**目标**: 制定产品策略

**使用 pm-skills**:
```
/strategy
```

**产出**: 产品愿景、竞争分析、市场定位

---

### 阶段 3: 规划 (Planning)

**目标**: 产出需求文档和开发计划

**使用 pm-skills**:
```
/write-prd
```

**同时创建 OpenSpec Change**:
```bash
openspec new change feature-xxx
```

---

### 阶段 4: 开发 (Development)

**目标**: 管理和执行开发任务

**使用 OpenSpec**:
```bash
# 查看状态
openspec status --change feature-xxx

# 添加任务
openspec show feature-xxx --json

# 验证
openspec validate --change feature-xxx

# 完成归档
openspec archive feature-xxx
```

**嵌入 Superpowers**（按需使用）:

| 场景 | 技能 | 命令 |
|------|------|------|
| 写测试先行的代码 | TDD | `superpowers:test-driven-development` |
| 遇到 bug 调试 | 调试 | `superpowers:systematic-debugging` |

---

### 阶段 5: 发布 (Launch)

**目标**: 规划产品发布

**使用 pm-skills**:
```
/plan-launch
```

---

## 常用命令速查

### pm-skills 命令

| 命令 | 用途 |
|------|------|
| `/discover` | 发现阶段 |
| `/strategy` | 策略规划 |
| `/write-prd` | 写 PRD |
| `/plan-launch` | 发布规划 |
| `/north-star` | 定义指标 |

### OpenSpec 命令

| 命令 | 用途 |
|------|------|
| `openspec init` | 初始化项目 |
| `openspec new change <name>` | 创建变更 |
| `openspec list` | 列出变更 |
| `openspec status` | 查看状态 |
| `openspec validate` | 验证 |
| `openspec archive` | 归档完成 |

---

## opsx:explore vs pm-skills 区别

### `/opsx:explore` - 技术探索

| 维度 | 说明 |
|------|------|
| **定位** | 探索模式 |
| **目的** | 思考、调研、技术选型 |
| **方式** | 自由思考、无固定流程 |
| **场景** | 理解问题、调研代码、方案比较 |

**例子**：
```
/opsx:explore real-time collaboration
→ 探讨实时协作的技术方案
→ 分析现有代码库
→ 比较 WebSocket vs SSE
→ 给出建议
```

### pm-skills - 产品工作流

| 阶段 | 命令 | 产出 |
|------|------|------|
| 发现 | `/discover` | 发现报告 |
| 策略 | `/strategy` | 产品愿景、竞争分析 |
| 规划 | `/write-prd` | PRD 文档 |
| 发布 | `/plan-launch` | 发布计划 |
| 指标 | `/north-star` | 北极星指标 |

### 使用场景对照

| 场景 | 用哪个 |
|------|--------|
| "这个功能怎么做？技术选型是什么？" | `/opsx:explore` |
| "这个想法值不值得做？" | `/discover` |
| "我们需要什么样的产品策略？" | `/strategy` |
| "帮我写个 PRD" | `/write-prd` |
| "怎么规划发布？" | `/plan-launch` |

### 一句话总结

- **`/opsx:explore`** = 技术探索（怎么做）
- **pm-skills** = 产品工作流（做什么）

**两者互补**：先用 pm-skills 想清楚"做什么产品"，再用 `/opsx:explore` 探索"怎么做出来"

---

## 最佳实践

1. **先想清楚，再动手**
   - 用 pm-skills 分析清楚再创建 OpenSpec change

2. **小步迭代**
   - 每个 change 不要太大

3. **及时归档**
   - 完成后立即 archive，保持整洁

4. **活用 skills**
   - 遇到问题随时用对应的 /pm-skills 命令

---

## 示例流程

```bash
# 1. 发现阶段
/discover
# 用户想要一个 AI 写作助手...

# 2. 策略阶段
/strategy
# 确定目标用户、竞争差异化...

# 3. 创建变更
openspec new change ai-writing-assistant

# 4. 写 PRD
/write-prd
# 产出需求文档...

# 5. 开发管理
openspec status --change ai-writing-assistant
openspec validate

# 6. 发布
/plan-launch
```

---

## 开始使用

```bash
# 在你的项目目录初始化
openspec init --tools claude

# 查看所有变更
openspec list

# 创建新功能
openspec new change your-feature-name
```

---

## Superpowers 集成

> 在开发阶段可以使用 Superpowers 技能增强开发效率

### 安装 Superpowers

```bash
npx skills add obra/superpowers
```

### 常用技能

| 技能 | 用途 | 阶段 |
|------|------|------|
| `superpowers:test-driven-development` | TDD 测试先行 | 开发 |
| `superpowers:systematic-debugging` | 系统化调试 | 开发/调试 |
| `superpowers:verification-before-completion` | 完成前验证 | 发布前 |

### 使用示例

```bash
# 开发新功能时，使用 TDD
superpowers:test-driven-development
# → 先写测试，再写实现代码

# 遇到 bug 时，系统化调试
superpowers:systematic-debugging
# → 4步根因分析
```
