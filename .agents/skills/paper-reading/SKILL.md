---
name: paper-reading
description: Read and explain research papers in English. Use when a user provides a PDF, arXiv or OpenReview link, paper title, or other paper link and requests a detailed summary, method or math explanation, experimental analysis, limitations, reproduction, counterexamples, later research, or follow-up ideas.
---

# PaperForge: Paper Reading (English)

## Usage

When the user provides a paper and asks to read or summarize it, use available paper-reading and search tools and address all 13 points in the prompt below in a single response. Do not introduce separate modes or additional analysis steps.

## Original Prompt (English translation)

Your task is to summarize this paper clearly, accessibly, deeply, and in detail (read the PDF and search arXiv and other available sources for the paper).

Your summary should be well structured and cover the following:
1. What research problem does the paper propose and address (search for and supplement relevant background when appropriate)? Why is this problem important? What value would solving it bring?
2. Has this problem been addressed before? What were the shortcomings of previous research?
3. Before formally explaining the method, reconstruct the authors' possible path of thinking. Do not use this paper's contributions as premises. Use only previously available background, failure modes, empirical observations, and related work. Think through and simulate the inspiration and intuition that might have led the authors to this idea, helping me understand how one could arrive at it from existing knowledge.
4. What is the intuition behind the proposed method? Explain the essence of the core idea clearly, concisely, and in plain language.
5. What exactly is the method? Explain the complete input → processing → output pipeline using a concrete example. Break it down into clear, understandable steps.
6. What are the core mathematical derivations (explain them step by step from scratch so I can understand the method theoretically)? If there are any, provide the necessary theoretical background (my math foundation is weak) and explain the underlying principles and intuition. If there are none, say so and skip this point. Use accurate Markdown syntax for all mathematical formulas so they render correctly.
7. How does the paper design experiments to validate its method and claims? Use the format: What question is being asked → What experiment tests it → What is the answer? Focus on the core experimental logic rather than excessive numerical details.
8. Summarize the main takeaways of the paper.
9. What is the paper's most vulnerable assumption?
10. If I had one week, what minimal reproduction experiment could I run to verify one of its claims?
11. If I wanted to challenge the paper, how would I design a counterexample?
12. Use search tools to investigate follow-up research on this paper. Are there subsequent extensions, rebuttals, or new insights?
13. Research and think carefully, then propose a follow-up idea based on the available information. It should be novel rather than incremental, driven by limitations of the method and unmet needs, and aimed at a new, valuable research direction.

Requirements:
* Refer to the writing styles of Andrej Karpathy and Kaiming He, aiming for a natural human voice.
* Make detailed, accurate claims. Every sentence should carry information; avoid vague statements and generic filler.
* Write fluently. Avoid overusing dashes and quotation marks, and keep the output clean and easy to read.
* Follow natural human reasoning. Avoid low-information AI-style constructions such as “not ... but ...”.
* Strictly distinguish four categories: claims explicitly made in the paper, established findings in related literature, reasonable evidence-based inferences, and speculation that remains uncertain. Never present an inference as a fact.
