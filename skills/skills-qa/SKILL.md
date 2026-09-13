---
name: skills-qa
description: >-
  当需要自动维护、质检、同步或推广用户自建 skills（含 HuiCheng/skills 仓库）时使用：对齐本地与 GitHub、跑 skill-eval、有必须修则阻塞。
---
# skills 质检维护

自动维护用户自建 skills 的质量与仓库同步。默认对象：本地 `pr` / `skill-eval`，以及 GitHub `HuiCheng/skills`（`pr-adversarial-review`、`skill-eval`）。

## 何时用

- 用户要求维护 / 质检 / 同步 skills
- 定时例行任务触发
- 刚改完某个 skill，准备推仓库或宣称可推广

## 质量门禁

1. **结构**：每个 skill 有 `name` + `description`（何时用）+ 可执行正文；description 不含助手私有细节。
2. **通用性**：正文不得绑死单一领域专名，除非该 skill 明确声明领域范围。
3. **盲评**：对行为向 skill，按 [skill eval 迭代](sand-workflow:skill-eval) 跑有 skill vs 无 skill；关键量规不低于对照；门禁不得被「改文档 / intentional split / CI deferred」绕过。
4. **同步**：本地与 `HuiCheng/skills` 正文应对齐（允许 frontmatter `name` 因平台差异不同）。漂移则先修再推。
5. **阻塞**：有必须修项时，不得推「可推广」结论，不得静默降级标准。

## 步骤

### 轻量巡检（工作日）

1. 列出本地自建 skills 与 `HuiCheng/skills` 目录。
2. 对比各 `SKILL.md` 正文哈希/关键 diff。
3. 无漂移且无用户待办：安静结束。
4. 有漂移：修好较弱一侧（通常以本地评测通过版为准），在 Mac 用 `gh` 推送到 `HuiCheng/skills`，并通知用户变更摘要。

### 深度质检（每周）

1. 对每个行为向 skill 跑一轮 [skill eval 迭代](sand-workflow:skill-eval)（新 fixture 或加难档）。
2. 记录分数、门禁是否安全、是否推广。
3. 不通过：开修复（改 skill → 再 eval），通过后再同步仓库。
4. 有结果才通知用户；全绿可短报一句。

### 变更后强制

任何 skill 正文修改后：先 eval，再决定是否推 GitHub。跳过 eval 不得宣称质量达标。

## 完成标准

- 本地与 GitHub 无未解释漂移
- 最近一次深度质检有落盘结论
- 未通过项有明确修复计划或已阻塞推广
