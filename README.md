# skills

Hui Cheng 的可安装 Agent Skills。兼容 [skills CLI](https://skills.sh) / `npx skills@latest add`。

## Skills

| 目录 | 名称 | 用途 |
|------|------|------|
| `skills/pr-adversarial-review` | 提 PR 对抗审查 | 开/更新 PR 前对抗式 diff 审查，姐妹路径 / 静默降级 / 假绿测试；有必须修则阻塞 |
| `skills/skill-eval` | skill eval 迭代 | 改完 skill 后盲评变体（含无 skill 对照），按门禁硬度决定是否推广 |
| `skills/skills-qa` | skills 质检维护 | 自动维护/同步/质检自建 skills；漂移对齐；eval 不过则阻塞推广 |

## Install

一次性装两个：

```bash
npx skills@latest add HuiCheng/skills --skill '*' -y
```

只装其中一个：

```bash
npx skills@latest add HuiCheng/skills --skill pr-adversarial-review -y
npx skills@latest add HuiCheng/skills --skill skill-eval -y
```

指定 Cursor：

```bash
npx skills@latest add HuiCheng/skills -a cursor --skill '*' -y
```

列出仓库里有哪些 skill：

```bash
npx skills@latest add HuiCheng/skills --list
```

## Layout

```
skills/
  pr-adversarial-review/SKILL.md
  skill-eval/SKILL.md
  skills-qa/SKILL.md
```

每个 skill 遵循 [Agent Skills](https://agentskills.io/) 格式：YAML frontmatter（`name` + `description`）+ markdown 正文。

## License

MIT
