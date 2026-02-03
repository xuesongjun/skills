# My Claude Code Skills

个人 Claude Code Skills 集合，用于跨电脑同步开发工作流。

---

## 安装方式

在 Claude Code 中运行：

```bash
# 添加 marketplace source
/plugin marketplace add xuesongjun/skills

# 安装 skill 集合（按需选择）
/plugin install dev-workflow@skills
/plugin install test-studio@skills
/plugin install code-quality@skills
```

---

## Skill 集合

### dev-workflow (开发工作流)

| Skill | 描述 | 触发词 |
|-------|------|--------|
| commit | Git 提交，生成中文提交信息 | `/commit` |
| save-progress | 存盘，保存开发进度到 CLAUDE.md | "存盘"、"收工" |
| sync-context | 读档，恢复上次开发上下文 | "同步进度"、"读档" |
| run | 启动 Test Studio 应用 | `/run` |

### test-studio (Test Studio 项目)

| Skill | 描述 |
|-------|------|
| fix-bug | 按标准流程修复 Bug |
| add-page | 添加新页面 |
| add-reg-group | 添加寄存器分组配置 |

### code-quality (代码质量)

| Skill | 描述 | 触发词 |
|-------|------|--------|
| clean-code-architect | 架构专家，代码质量约束 | 编写新功能、定义 API |
| quick-refactor | 重构助手 | "重构"、"优化代码" |
| test-master | 测试专家 | "写测试"、"测试这个函数" |

---

## 目录结构

```
my_skills/
├── .claude-plugin/
│   └── marketplace.json      # ⭐ 分组配置文件
├── skills/
│   ├── commit/SKILL.md
│   ├── save-progress/SKILL.md
│   ├── sync-context/SKILL.md
│   ├── run/SKILL.md
│   ├── fix-bug/SKILL.md
│   ├── add-page/SKILL.md
│   ├── add-reg-group/SKILL.md
│   ├── clean-code-architect/SKILL.md
│   ├── quick-refactor/SKILL.md
│   └── test-master/SKILL.md
└── README.md
```

---

## 维护指南

### 1. 添加新 Skill

**步骤 1**: 创建 skill 目录和文件

```bash
mkdir skills/my-new-skill
```

**步骤 2**: 创建 `skills/my-new-skill/SKILL.md`

```markdown
---
name: my-new-skill
description: |
  技能描述，说明何时使用此技能
---

# 技能标题

## 执行步骤

1. 步骤一
2. 步骤二
```

**步骤 3**: 将新 skill 添加到分组（编辑 `.claude-plugin/marketplace.json`）

```json
{
  "plugins": [
    {
      "name": "dev-workflow",
      "skills": [
        "./skills/commit",
        "./skills/my-new-skill"   // ← 添加到对应分组
      ]
    }
  ]
}
```

**步骤 4**: 提交并推送

```bash
git add .
git commit -m "添加新 skill: my-new-skill"
git push
```

---

### 2. 修改分组

分组在 `.claude-plugin/marketplace.json` 中定义：

```json
{
  "name": "skills",
  "owner": {
    "name": "xuesongjun",
    "email": "xuesongjun@example.com"
  },
  "plugins": [
    {
      "name": "dev-workflow",           // ← 分组名称
      "description": "开发工作流",        // ← 分组描述
      "source": "./",
      "strict": false,
      "skills": [                        // ← 该分组包含的 skills
        "./skills/commit",
        "./skills/save-progress",
        "./skills/sync-context",
        "./skills/run"
      ]
    },
    {
      "name": "test-studio",
      "description": "Test Studio 项目专用",
      "skills": [
        "./skills/fix-bug",
        "./skills/add-page",
        "./skills/add-reg-group"
      ]
    },
    {
      "name": "code-quality",
      "description": "代码质量",
      "skills": [
        "./skills/clean-code-architect",
        "./skills/quick-refactor",
        "./skills/test-master"
      ]
    }
  ]
}
```

### 分组操作示例

**添加新分组**:
```json
{
  "name": "new-group",
  "description": "新分组描述",
  "source": "./",
  "strict": false,
  "skills": [
    "./skills/skill-a",
    "./skills/skill-b"
  ]
}
```

**将 skill 移到其他分组**:
从原分组的 `skills` 数组中移除，添加到目标分组的 `skills` 数组中。

**合并所有 skill 到一个分组**:
```json
{
  "plugins": [
    {
      "name": "all",
      "description": "所有 skills",
      "skills": [
        "./skills/commit",
        "./skills/save-progress",
        // ... 所有 skills
      ]
    }
  ]
}
```

---

### 3. SKILL.md 文件格式

```markdown
---
name: skill-name              # 必填：skill 名称（kebab-case）
description: |                # 必填：skill 描述
  详细描述，说明何时使用此技能
---

# 标题

## 触发词（可选）
- 关键词1
- 关键词2

## 执行步骤

1. 步骤描述
2. 步骤描述

## 注意事项

- 注意点1
- 注意点2
```

---

### 4. 同步到其他电脑

在新电脑上：

```bash
# 1. 添加 marketplace（只需一次）
/plugin marketplace add xuesongjun/skills

# 2. 安装需要的分组
/plugin install dev-workflow@skills
/plugin install test-studio@skills
/plugin install code-quality@skills
```

更新后重新安装即可获取最新版本。

---

## 本地开发

```bash
# 克隆仓库
git clone https://github.com/xuesongjun/skills.git

# 修改后推送
git add .
git commit -m "更新 skill"
git push
```

---

## 参考资料

- [Agent Skills 官网](https://agentskills.io/home)
- [Agent Skills Specification](https://agentskills.io/specification)
- [Anthropic Skills 仓库](https://github.com/anthropics/skills)
