# go-deeper

Turn a task into a **deeper** version — not a bigger one. A minimal, bilingual (English / 中文) agent skill built around the "golden depth prompt" from Felix Rieseberg's essay *How to be more ambitious: A tutorial for humans with models* (2026-10-13).

## Source & attribution

All ideas and the golden prompt come from:

- **Felix Rieseberg**, "How to be more ambitious: A tutorial for humans with models", published 13 October 2026 on felixrieseberg.com.
- Original article: <https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/>
- Felix is an engineering manager at Anthropic, where he has led engineering for Claude.ai, Cowork, and Claude Code Desktop. He is also co-maintainer of Electron.

The English golden prompt in `go-deeper/SKILL.md` is quoted verbatim from that article, with attribution. The Chinese rendering is a faithful translation of the same passage.

A related community project — [robonuggets/be-ambitious](https://github.com/robonuggets/be-ambitious) — turns the full four-dimension framework (speed / altitude / depth / range) into a Claude skill. This repo is intentionally narrower: it packages only the **depth** dimension as a lightweight, bilingual skill.

## What the skill does

When triggered (e.g. "go deeper on this", "更深度的版本", "把这个任务做得更有深度"), the agent:

1. Answers four questions: what a top professional would do that you didn't ask for; the rawest material to start from; the specific methods and tools they would use; and what outside validator proves the result right.
2. Rewrites your prompt to demand exactly that, in your language.
3. Offers to execute the rewritten prompt.

The full golden prompt (English + 中文对照) is embedded in the skill body, so it works out of the box with any agent that supports skills.

## Install

Copy the `go-deeper/` directory into your agent's skills directory. For Kimi / Claude-compatible agents:

```bash
cp -r go-deeper ~/.agents/skills/   # or your platform's skills path
```

Trigger it by saying things like "go deeper on this task" or "帮我把这个任务做成更深度的版本".

## License

Code and packaging are MIT (see [LICENSE](LICENSE)). The quoted golden prompt and the underlying methodology remain the intellectual property of Felix Rieseberg and are included here with attribution under fair-use quotation; they are **not** covered by the MIT license.
