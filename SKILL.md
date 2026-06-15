---
name: paper-reading
description: >
  Use this skill whenever a user wants to deeply read, analyze, understand, or summarize a research paper, preprint, or academic article. Triggers include: sharing an arXiv link or PDF, pasting a paper title or abstract and asking for a breakdown, saying "help me read this paper," "summarize this paper," "explain this paper," "analyze this paper," "what does this paper say," "walk me through this," or anything that implies the user wants to extract deep understanding from a piece of academic work. Also trigger when the user asks you to critique, attack, or find weaknesses in a paper, or when they want follow-up research ideas inspired by a paper. This skill applies across all technical domains — machine learning, NLP, computer vision, systems, biology, physics, economics, etc. The goal is not passive summarization but active reconstruction of the author's reasoning, honest critique, and generative thinking.
---

# Paper Reading Skill

This skill turns a passive read into an active intellectual exercise. The goal is not to parrot the abstract — it's to reconstruct how the authors got the idea, understand the method at a mechanistic level, and then stress-test it. Think Andrej Karpathy walking through a paper on his blog: concrete, specific, honest about what's uncertain.

## What you need from the user

Before starting, identify the paper. The user might provide:
- A URL (arXiv, ACL Anthology, OpenReview, PapersWithCode, a lab page, etc.)
- A PDF or file attachment
- A title or title + abstract

If a URL is given, fetch the full paper text first. If only a title is given, web-search for the paper, find the canonical source (arXiv preferred), and fetch the full text. Do not proceed from an abstract alone — the method section, experimental details, and appendices are essential.

## How to read before writing

After fetching the paper:
1. Skim the abstract, introduction, related work, method, experiments, and conclusion in one pass.
2. Identify the core technical claim, the key experiment that proves it, and the most important baseline comparison.
3. Search for 2–3 closely related prior works if context is needed to understand the novelty. Do this before writing the summary — it prevents misrepresentation of what's new.

Then produce the full analysis below.

---

## Output structure

Work through all 12 sections in order. The order matters: background before method, method before experiments, critique after understanding. Do not reorder or skip sections (except §6, which may be skipped if there is no formal math).

Write in flowing prose. Use paragraph structure, not bullet-point lists, except where a structured list genuinely aids comprehension (e.g., listing experimental results in §7). Avoid em-dashes. Avoid scare quotes. Every sentence should carry information.

---

### § 1 — The problem and why it matters

State the research question the paper addresses. Be specific: name the task, the domain, the failure mode, the gap. Then explain why solving it is valuable — what downstream capability, product, or scientific understanding it unlocks. If the significance is non-obvious, do a brief web search to calibrate (e.g., how widely used is the system this paper targets?).

Distinguish between what the paper explicitly claims is its motivation and what you infer from the broader context.

---

### § 2 — Prior work and its limitations

Describe the state of the art before this paper. Name the most relevant prior methods and what they achieve. Then be precise about why they fall short: is it a fundamental limitation of the approach, a missing assumption, a practical bottleneck, or a gap in evaluation? 

Avoid the lazy framing "prior work didn't consider X." Explain *why* prior work didn't consider it — was it technically infeasible, was it overlooked, or was the problem not yet recognized?

---

### § 3 — Reconstructing the author's thought process

This is the most important section. The goal is to reverse-engineer how a thoughtful researcher, staring at the prior work and the failure modes, could have arrived at this paper's idea — without using the paper's own contributions as a starting point.

Work only from what was knowable before this paper: published methods, observed failure patterns, empirical intuitions, and analogies from adjacent fields. Then simulate the intellectual journey:

- What phenomenon or failure would have been frustrating or puzzling to an expert in this space?
- What analogies or insights from related areas could have suggested a new approach?
- What would a researcher have tried first, and why would it not have worked?
- What shift in framing or assumption unlocks the core idea?

Be honest about what is your reconstruction versus what the paper explicitly describes as its motivation. Phrases like "one plausible path is..." or "the authors hint at this by..." are appropriate here.

---

### § 4 — The core intuition

In 2–4 sentences, state the essential idea. Strip away the formalism, the ablations, and the engineering details. What is the one insight that makes this method work where prior work didn't? If you can't state it in plain language, the explanation isn't done yet.

---

### § 5 — The method in detail

Explain the full technical approach. Structure it as an end-to-end pipeline: what goes in, what computations happen, what comes out. Use a concrete, realistic example to ground the explanation — invent plausible inputs and trace them through every step. Make explicit:

- What each component does and why it's designed that way
- What design decisions were made and what the alternatives would have been
- Where the method is simple and where it has meaningful complexity

---

### § 6 — Mathematical foundations (skip if no formal math)

If the paper involves non-trivial mathematics (derivations, proofs, probabilistic formulations, optimization objectives), explain the key steps. Assume the reader is intelligent but not a specialist: define terms, explain why each step follows from the previous, and connect the math to the intuition from §4. If a derivation has a clever trick, name it and explain why it works.

If the paper is primarily empirical or system-oriented with no substantial formal theory, say so and skip this section.

---

### § 7 — Experimental design and results

For each major claim the paper makes, describe the experimental setup used to test it:

- What question is the experiment asking?
- What is the experimental design (datasets, baselines, metrics, controls)?
- What does the result show, and does it convincingly answer the question?

Keep this focused on the logic of the experimental design, not on listing numbers. A reader should understand what was proven and how strongly, not memorize benchmark scores.

---

### § 8 — Takeaways

Summarize what this paper contributes to its field. State this in terms of what you now know that you didn't before — a new capability, a new understanding, a new tool, a new way of framing a problem. Be specific about who should care about this paper and why.

---

### § 9 — The most vulnerable assumption

Every method rests on assumptions. Identify the single most important one that, if it failed, would undermine the core contribution. Explain precisely why this assumption might not hold in practice, and what evidence (or lack thereof) the paper provides for it.

Do not list every limitation. Find the one assumption whose failure would be most damaging.

---

### § 10 — Minimum reproducible experiment

If someone had one week and a standard research compute budget, what is the smallest experiment that could verify the paper's central claim? Specify: what data to use, what to implement, what to measure, and what result would constitute evidence for or against the claim. Prefer an experiment that doesn't require reproducing the full system from scratch.

---

### § 11 — The strongest counterargument

Design the most compelling attack on this paper. This is not about finding typos or minor ablation gaps — it's about finding an experiment, a theoretical argument, or a class of real-world cases that would genuinely challenge whether the method works as claimed. A good counterargument either proposes a specific alternative explanation for the results or identifies conditions under which the method would predictably fail.

---

### § 12 — A follow-up research idea

Based on your understanding of the method's core limitation (§9) and the gap it leaves open, propose one non-incremental research idea. This is not "extend the method to domain X" or "add a module to handle case Y." It is a new framing, a new objective, or a new connection to an adjacent problem that could open a genuinely different research direction.

Ground the idea in: (a) what limitation or unmet need motivates it, (b) what prior work or technique from a neighboring area it could draw on, and (c) what a plausible first experiment would look like. Distinguish clearly between what you're proposing and what is already known.

---

## Information source discipline

Throughout the entire analysis, strictly distinguish between four types of claims:

- **Paper states**: the authors explicitly claim or show this
- **Prior work establishes**: this is a documented result in the existing literature (cite if possible)
- **Reasonable inference**: this follows logically from what the paper shows, but is not stated explicitly
- **Speculation**: this is your hypothesis, not grounded in direct evidence

Never present an inference as a fact, and never present speculation as an inference. When you are uncertain which category a claim belongs to, say so.

---

## Style

Write the way Andrej Karpathy writes about technical material: concrete, direct, willing to say "this was annoying" or "this was clever." Start from a real technical situation, name the problem precisely, show the failure mode before giving the solution. Avoid filler phrases like "it is worth noting that" or "this is significant because." Every sentence earns its place.

Follow Kaiming He's discipline in technical writing: state the claim, then the evidence. Do not decorate before substantiating. Structure aids understanding; decoration does not.

Use American English throughout.
