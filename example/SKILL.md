---
name: my-example-skill
description: 示例技能：演示 DSH 衍生技能的标准结构 / Example skill: demonstrates the standard DSH derivative skill structure
---

# 示例技能 / Example Skill

本技能演示 DeepSeek Harness 衍生技能的编写规范：front-matter 中的 name 与双语 description、正文、何时使用、工作流。

This skill demonstrates the authoring conventions for DeepSeek Harness derivative skills: front-matter with name and bilingual description, body, when-to-use, and workflow.

## When to use / 何时使用

当需要把重复性检查或流程固化为可复用技能时使用本模板。Use this template whenever you want to codify a repeatable check or process into a reusable skill.

## Workflow / 工作流

1. 定义技能 id 与双语描述（front-matter）。
2. 编写正文：说明技能目的与用法。
3. 补充 When to use 与 Workflow。
4. 保存到 $DSH_HOME/skills/<skill-id>/SKILL.md。

## References / 参考

- Hermes Harness DSH 快速上手：dsh-starter-kit
- 作者: h565656445 (GitHub)