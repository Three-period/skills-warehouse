# Skills Warehouse

个人 AI 协作规则与可独立调用的产品工作 Skills。

## 结构

- **RULES.md**：个人沟通与协作原则。与所有 Skills 分离；是否生效由使用者在对应平台主动配置。
- **skills/requirement-clarification/SKILL.md**：需求调研与澄清。
- **skills/business-process-modeling/SKILL.md**：业务流程建模。
- **skills/business-specification/SKILL.md**：业务规格设计。
- **skills/product-design-prd/SKILL.md**：产品方案与PRD。
- **skills/product-review/SKILL.md**：产品方案评审。
- **skills/b2b-interaction-design/SKILL.md**：B 端交互设计与一致性规范。
- **skills/b2b-business-logic/SKILL.md**：原型业务状态、门禁与跨模块数据联动。
- **skills/prototype-quality-audit/SKILL.md**：已实现原型的需求追踪、实测证据与回归审计。

每个 Skill 都是完整、独立的工作单元。**不存在必须先调用其他 Skill 的顺序**；不要求读取其他文件夹、历史项目或个人规则；不内置训练模式。

## 每一个 Skill 的构建规范

每个 Skill 单独放在与名称一致的文件夹下，只需一个 SKILL.md 即可运行。

**文件头**（基于 Agent Skills 通用格式）：

~~~yaml
---
name: business-process-modeling
description: 说明该Skill能做什么、什么时候使用以及主要边界。
---
~~~

**文件正文统一七部分**：

1. **定位与适用范围**：解决什么任务；什么情况下不使用。
2. **输入识别**：需要哪些资料；缺少资料时如何处理。
3. **执行步骤**：从原始信息到结果的具体方法和判断依据。
4. **关键规则**：不可违反的业务约束和逻辑边界。
5. **输出规范**：交付的结构、格式、图表选择及简短示例。
6. **质量检查**：交付前能够逐项检查的标准。
7. **异常处理**：资料不足、规则冲突、失败、局限情况下怎么处理。

以 business-process-modeling 为模板，其余 Skill 采用相同构建方式，但**不能复制与自身任务无关的业务内容**。

## 独立性验收

为每个 Skill 单独测试：
1. 只提供本 Skill 和一份原始输入，不提供其他 Skill。
2. 能独立识别任务、处理足量输入并形成可用输出。
3. 缺失信息时标记待确认，能够安全继续的部分不阻塞。
4. 输出符合自身适用范围，不越界接管其他任务。
5. 新业务场景下仍然可用，不依赖代码检视等特定项目。

## 跨平台使用

本仓库是**源文件仓库**，上传 GitHub 本身不等于自动安装。

- 在支持 Agent Skills 的运行环境中，把单个 Skill 文件夹放入该环境支持的 Skill 路径。
- Codex 常用项目目录：.agents/skills/。
- Claude Code 常用项目目录：.claude/skills/。
- ChatGPT 的可用 Skill 入口依当前产品和账号能力而定；可以按平台支持方式导入或手动使用这些指令。
- RULES.md 需要单独复制/接入对应平台的全局或项目指令，不能假定会被自动读取。

以上路径仅用于适配说明，不改变仓库中每个 Skill 的独立性。
