# bk-skills

Agent skills by iambaangkok.

| Skill | What it does |
|---|---|
| [academic-writing](skills/academic-writing/SKILL.md) | Write, edit, or review proofs and papers in math and theoretical CS. Plain English, no filler, every step justified, math that renders in Markdown or LaTeX. |

## Install

Paste this into Claude Code:

```text
Install the academic-writing skill from https://github.com/iambaangkok/bk-skills. Copy the folder skills/academic-writing into ~/.claude/skills/academic-writing so that ~/.claude/skills/academic-writing/SKILL.md exists. Then tell me to restart Claude Code.
```

Or run:

```bash
npx skills add iambaangkok/bk-skills
```

## Use: academic-writing

1. Type `/academic-writing` in Claude Code. It stays on for the rest of the session.
2. Ask for one of three things:
   - **Draft**: "Write a proof that every tree with n vertices has n - 1 edges."
   - **Edit**: "Edit section 3 of `paper.md`." It changes only text that breaks a rule.
   - **Review**: "Review the proof of Lemma 2 in `paper.tex`." It lists problems without changing the text.
3. Type `stop academic mode` to turn it off.

Output is Markdown with TeX math (renders on GitHub and Claude chat) unless the file is `.tex`.
