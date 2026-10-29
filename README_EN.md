# PaperForge

[简体中文](./README.md) | [English](./README_EN.md)

**An active paper-reading skill that reconstructs author reasoning, explains methods mechanistically, stress-tests assumptions, and generates follow-up research ideas.**

---

## Files

| File | Description |
| --- | --- |
| [Chinese Skill](./.agents/skills/paper-reading-zh/SKILL.md) | Chinese paper-reading Skill in the Agent Skills format |
| [English Skill](./.agents/skills/paper-reading/SKILL.md) | English paper-reading Skill in the Agent Skills format |
| [System_Prompt.txt](./System_Prompt.txt) | Copyable system prompt for ChatGPT / Claude custom instructions |

## How to Use

### Option A: Claude/Codex Skill

Install either the [Chinese Skill](./.agents/skills/paper-reading-zh/SKILL.md) or [English Skill](./.agents/skills/paper-reading/SKILL.md) under the corresponding skills directory. Both use a standard `SKILL.md` with YAML frontmatter.

**Core Reading (Sections 1–8)** is the default. It covers the research problem, prior work, reconstructed reasoning, intuition, pipeline, math, experimental evidence, and takeaways. **Research Deep Dive (Sections 9–13)** adds vulnerable assumptions, a one-week reproduction, counterexamples, subsequent research, and a follow-up research idea. For a focused question, the agent answers that question without forcing all thirteen sections.

The previous version is saved at [backup/pre-skills-v2-2026-10-29](https://github.com/FeijiangHan/PaperForge/tree/backup/pre-skills-v2-2026-10-29).

Personal note: I've found ChatGPT better at explaining papers than Codex or Claude Code, at least for my reading workflow.

### Option B: System Prompt (my personal recommendation)

Copy [System_Prompt.txt](./System_Prompt.txt) into either:

- **Method 1:** Project → Custom Instructions. Then send a paper link, title, or PDF without pasting the prompt every time.
- **Method 2:** Paste the prompt directly into a conversation, then provide a paper link, title, or PDF.

I used Method 1 for a long time and found it convenient. Recently, Method 2 seemed to produce better summaries. I'm not sure whether the difference is caused by the prompt's position in the instruction hierarchy.

**One-click copy version (English translation of the original prompt in the Chinese README):**

```txt
Your task is to explain a research paper clearly, accessibly, deeply, and in detail. Read the PDF and search sources such as arXiv when available.

Organize your answer around these questions:
1. What research problem does the paper address? Why does it matter, and what value would solving it bring? Research the background when useful.
2. Was the problem addressed before? What specifically was missing from earlier work?
3. Before explaining the method, reconstruct a plausible path to the idea using only knowledge, failures, observations, and prior work available before this paper. Help me understand how a researcher could have arrived at this idea. Do not claim this is the authors' actual thought process.
4. What is the method's core intuition? Explain the essential idea concisely and in plain language.
5. How does the method work? Walk through a concrete input-to-output example and the full pipeline.
6. If the paper contains meaningful math, explain its core derivation from the foundations and provide intuition for each step. Assume my mathematical background is limited. Use valid Markdown math notation. Otherwise, skip this section.
7. How do the experiments test the claims? Use: question → experiment → result and what it establishes. Focus on experimental logic rather than excessive numbers.
8. Summarize the main takeaways.

For a quick paper reading, stop after Section 8. If I want to pursue the paper, continue with:
9. What is the most vulnerable assumption?
10. What small experiment could I run within one week to test a central claim?
11. What is the strongest counterexample I could design?
12. Search for later work: extensions, criticisms, rebuttals, and updated understanding.
13. Propose a potentially novel and valuable follow-up research idea grounded in a limitation or unmet need, rather than a minor incremental change. Verify relevant prior work before claiming novelty.

Style:
- Use transferable traits of Andrej Karpathy's and Kaiming He's technical clarity.
- Make concrete, accurate claims; every sentence should carry information.
- Write fluidly and avoid unnecessary dashes, quotation marks, formulaic contrasts, and generic filler.
- Separate claims explicitly stated in the paper, results established in prior literature, evidence-based inferences, and untested speculation. Do not pass inference off as fact.
```

**October 27, 2026 update:**

1. Earlier versions of the prompt could miss visual understanding. Figure 1, method diagrams, and experimental plots can explain a paper more effectively than text alone, and also help develop a sense for good research figures. You could also experiment with interactive HTML explanations or AI-generated explainer videos.
2. A full, lengthy analysis is wasteful if I lose interest in the paper. A better first step can be to propose one or two research questions based on the paper so I can decide whether I want to read further. Having a question to solve makes reading more purposeful.
3. With a ChatGPT browser extension, you can discuss a blog post or paper alongside the page instead of copying its URL into another chat.

### Option C: Evolve your own paper-reading workflow

If you already have your own prompts or skills, ask an agent to review this repository and combine the best parts of both workflows:

1. Compare your current prompt with PaperForge.
2. Preserve the parts of your existing workflow that work best for you.
3. Combine them into a reading workflow tailored to your research interests and preferences.

Pay particular attention to Section 3 (reconstructing a plausible path to the idea), Section 9 (most vulnerable assumption), Section 10 (minimal reproduction), and Section 11 (strongest counterexample).

PaperForge can be the starting point rather than the final version of your reading workflow.

### Option D: Adapt the prompt for humanities and social sciences

The current version is primarily designed for experimental and methodological STEM papers. For a humanities or social-science field, you can adapt it by asking a reasoning model with web search:

> https://github.com/FeijiangHan/PaperForge
>
> Research how reading papers in [specific humanities or social-science field] differs from reading technical STEM papers. Then propose changes to the skills in this repository for that field. Preserve the central ideas: reconstructing the reasoning behind a study, unpacking its argument, identifying assumptions, and finding open questions.

Possible disciplines include history, sociology, political science, philosophy, anthropology, education, communication, economics, law, and literary studies.

---

## Reference

My Xiaohongshu post: [The best prompt I've found after two and a half years of reading papers with AI](https://www.xiaohongshu.com/discovery/item/6a300c2e00000000060363b6?source=webshare&xhsshare=pc_web&xsec_token=ABYfMQEP9MGgfWyKvWBWs6xOMpOBKCFU80meDyRtv5h5A=&xsec_source=pc_share)
