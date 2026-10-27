---
name: go-deeper
description: Turn a task or prompt into a deeper (not bigger) version using Felix Rieseberg's golden depth prompt — bilingual English/中文. Use when the user says "go deeper on this", "更深度的版本", "不是更大而是更深", "帮我把这个任务/提示词做得更有深度", "what would a top expert do here", "加上外部验证", or otherwise wants a task pushed to field-expert level with outside validation before executing it.
---

# Go Deeper

Turn a task into a **deeper** version, not a bigger one. Source: Felix Rieseberg (EM at Anthropic), "How to be more ambitious: A tutorial for humans with models", 2026-10-13. <https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/>

Core insight: telling a model to "act like an expert" only changes its vocabulary, not its methods. Depth means making it use the real tools, raw materials, and methods of the best professionals in the field — with an outside judge.

## Workflow

When this skill triggers:

1. Identify the user's actual task or prompt.
2. Work through the four questions below (reason it out, or ask the model to answer them explicitly):
   1. What would a top professional in this field do here that the user is not asking for?
   2. What is the rawest material they would start from, instead of conclusions already digested by others?
   3. What specific methods, statistical models, and tools would they use?
   4. What — other than the user or the model — would show the result is right? (runnable tests, raw-data checks, benchmarks, reproducible artifacts)
3. Rewrite the user's prompt to demand exactly that. **Write the rewritten prompt in the user's language** (中文用户给中文版，English users get English).
4. Present the rewritten prompt and offer to execute it.

## The golden prompt (verbatim, bilingual)

English original:

```
I want a deeper version of this task, not a bigger one.
Before rewriting it:
(1) say what a top professional in this field would do here that I'm not asking for;
(2) name the rawest material they would start from instead of what has already been digested for me;
(3) name the specific methods and tools they would use;
(4) say what, other than you or me, would show the result is right.
Then rewrite my prompt to ask for exactly that.
```

中文对照:

```
我想把这项任务做成更深度的版本，不要仅仅做成更庞大的版本。
在重写我的任务提示词之前，请先完成以下四件事：
(1) 明确指出该领域最顶尖的专家在这里会做些什么，而这些是我当前根本没有想到的；
(2) 指出他们会从什么样最原始的底层素材和数据开始，而不是用别人已经为我消化过的二手结论；
(3) 列出他们会具体使用的专业工具、统计模型与工作方法；
(4) 说明除了你和我之外，有什么客观的外部标准或工具能够证明最终的结果是完全正确的。
梳理清楚以上四点后，请重新改写我的提示词，完全按照这个顶尖专家的标准向你发起提问。
```

If the user hands over a task directly, you may answer the four questions yourself and deliver the rewritten prompt in one step; otherwise, give the user the golden prompt to paste into a fresh chat.

## Guardrails

- **Outside judge is mandatory.** Never let the model grade its own output — in 2026 this still produces self-satisfied errors. The rewritten prompt must name a concrete external validator (test suite, raw-data reproduction, benchmark, reproducible artifact).
- **Watch review cost.** The deeper the task, the higher the human cost of verifying the output. For long-horizon tasks, require checkpoints or staged verification in the rewritten prompt.
- **Not for open-ended creative work.** Where wandering and serendipity are the point, depth framing can kill the magic; offer it only for craft polish (e.g., format drudgery), not for the core creative act.
- **Environment over wording.** If the task needs data access, permissions, or test environments to go deep, say so — a clever prompt cannot substitute for missing scaffolding.
