# My Claude Code Skills

个人 Claude Code Skills 集合，用于跨电脑同步开发工作流。

## 安装方式

在 Claude Code 中运行：

```bash
# 添加 marketplace source
/plugin marketplace add xuesongjun/skills

# 安装 skill 集合
/plugin install dev-workflow@skills
/plugin install test-studio@skills
/plugin install code-quality@skills
```

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

## 目录结构

```
my_skills/
├── .claude-plugin/
│   └── marketplace.json      # Marketplace 配置
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

## 参考
- [Agent Skills ](https://agentskills.io/home)

- [Agent Skills Specification](https://agentskills.io/specification)

- [skills](https://github.com/anthropics/skills)

- [Agent Skills](https://github.com/agentskills/agentskills)
