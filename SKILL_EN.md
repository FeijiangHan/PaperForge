---
name: paper-reading
description: >
  Use this skill when the user wants to deeply read, understand, summarize, analyze, critique, or extend a research paper, preprint, or academic article in English. Trigger it when the user provides an arXiv link, PDF, OpenReview page, ACL Anthology link, PapersWithCode page, paper title, abstract, or asks things like help me read this paper, summarize this paper, analyze this paper, explain this paper, help me understand this paper, find weaknesses in this paper, design counterexamples, or propose follow-up ideas. This skill applies across technical and scientific domains, including machine learning, NLP, computer vision, systems, biology, physics, economics, and related areas. The goal is not to restate the abstract, but to reconstruct the authors' reasoning, explain the method, evaluate the evidence, identify vulnerable assumptions, and propose research directions with clear, accurate English.
  
---

# Paper Reading Skill

## Preparation

First obtain the full text of the paper before writing the analysis.

The user may provide:

- A URL, such as arXiv, ACL Anthology, OpenReview, PapersWithCode, a publisher page, or a lab page
- A PDF or file attachment
- A paper title
- A title plus abstract

If the user provides a URL, fetch the full text first. If the user provides only a title, web search for the canonical version, preferably arXiv or the official venue version. If only the abstract is available, state that the analysis is provisional and explain which parts cannot be verified.

Do not answer from the abstract alone. The method, experimental details, figures, limitations, and appendix often contain the real contribution and the real problems.

After obtaining the full text, read the abstract, introduction, related work, method, experiments, conclusion, and appendix when needed. Before writing, identify three things:

1. The paper's central technical claim.
2. The key experiment or argument supporting that claim.
3. The most important baseline or prior work comparison.

If the novelty is unclear, search for 2 to 3 closely related papers to calibrate what is actually new. Do not claim novelty based on intuition, and do not invent related work to generate a follow-up idea.

------

## Output structure

Your task is to produce a clear, readable, deep, and detailed paper analysis.

Output the following 12 sections in order. The order matters: background before method, method before experiments, understanding before critique. Do not skip any section except Section 6.

Write mostly in flowing paragraphs. Use bullet points only when they genuinely improve structure, such as for experimental design, pipeline steps, or a minimum reproducible experiment. Avoid overusing dashes, quotation marks, parentheses, and low-information transitions. Every sentence should carry information.

------

### § 1 - Research problem and importance

What research problem does the paper propose and solve? Why is this problem important? What value would solving it bring?

If the importance is not obvious, do a small amount of background research to provide context.

------

### § 2 - Prior work and limitations

Had this problem been addressed before? Why were previous approaches insufficient?

Name the most relevant prior methods, systems, datasets, or theoretical results, and briefly explain what they can already do. Then explain precisely why they are not enough: is the limitation in the method itself, a failed assumption, high engineering cost, an evaluation gap, or a problem that had not yet been clearly defined?

Avoid the vague framing prior work did not consider X. Explain why X was not considered: was it technically infeasible, too expensive, overlooked, or not yet a visible problem?

------

### § 3 - Reconstructing the authors' thought process

Before explaining the method, reverse-engineer the authors' possible path of thought.

Do not use the paper's own contribution as the premise. Use only the background, failure modes, empirical observations, theoretical clues, and related work that existed before this paper. The goal is to simulate how a serious researcher could move from existing knowledge to this paper's idea.

------

### § 4 - Core intuition

Explain the method's core intuition in 2 to 4 sentences. Remove the formalism, ablations, and engineering details.

What is the key idea that made prior methods fail and this method work? If this cannot be explained in plain language, the understanding is not finished.

------

### § 5 - Method and full pipeline

What is the concrete method proposed by the paper? Explain it with a realistic example: input, processing, and output. Use clear structure when helpful.

------

### § 6 - Core mathematical derivation

What is the paper's core mathematical derivation, if it has one? Explain it step by step from the theoretical side.

If there is formal math, provide the necessary background for a reader with weaker math preparation. Explain the foundation of the theory and the intuition behind each formula. If there is no meaningful formal derivation, say so and skip this section.

------

### § 7 - Experimental design and conclusions

How does the paper design experiments to verify its method and claims?

Use this format: what question is being asked -> what experiment is designed to answer it -> what answer does the experiment give.

Do not include too many numerical details. Focus on the core experimental logic.

------

### § 8 - Takeaways

Summarize the paper's takeaways.

------

### § 9 - Most vulnerable assumption

Every method depends on assumptions. Identify the most important one: if it fails, the paper's central contribution would fail.

Explain precisely why this assumption may not hold in practice, and what evidence the paper provides for it, or what evidence is missing.

Do not list every limitation. Find the assumption whose failure would be most damaging.

------

### § 10 - Minimum reproducible experiment

If I had one week, what minimum experiment could I run to test the paper's central claim?

Specify what data to use, what to implement, what to measure, and what result would support or refute the claim. Prefer an experiment that does not require reproducing the full system.

------

### § 11 - Strongest counterexample

If I wanted to argue against this paper, how would I design a counterexample?

Design the strongest attack on the paper. Find an experiment, theoretical argument, or real-world scenario that can genuinely challenge whether the method works as claimed.

A good counterexample either gives a concrete alternative explanation for the results or identifies conditions where the method should predictably fail.

------

### § 12 - Follow-up research idea

Study the research taste and problem impact of top conference best papers when useful.

Based on the core limitation in Section 9, propose one non-incremental novel research idea. It should not be simply extending the method to domain X or adding a module for case Y. It should be a new framing, a new objective, or a new connection to a neighboring problem that could open a genuinely different direction.

Explain: (a) what limitation or unmet need motivates the idea, (b) what neighboring field, method, or tool it could draw from, and (c) what the first experiment would look like. Clearly separate your proposal from existing work.

------

## Source discipline

Throughout the analysis, strictly distinguish four types of claims:

- **Paper states**: the authors explicitly claim or show this.
- **Prior work establishes**: this is a documented result in the existing literature. Cite when possible.
- **Reasonable inference**: this follows logically from the paper's evidence, but is not explicitly stated.
- **Speculation**: this is your hypothesis and is not directly supported by evidence.

Do not present inference as fact. Do not present speculation as inference. If you are unsure which category a claim belongs to, say so directly.

------

## Style

The default output language is English. Preserve standard technical terms such as attention, fine-tuning, ablation, retrieval, policy gradient, representation, and benchmark.

Use Andrej Karpathy and Kaiming He as style references, but only for transferable technical writing traits.

Requirements:

- Start from a concrete technical situation, not a floating summary.
- Name the problem directly. Show the failure mode before explaining the method.
- Use concrete nouns, actions, and numbers. Avoid abstract adjectives.
- State the claim first, then the evidence.
- Keep uncertainty visible. Do not pretend everything is settled.
- Make every sentence informative. Avoid empty generalities.
- Use flowing paragraphs and avoid overly templated bullet points.
- Avoid overusing dashes, quotation marks, parentheses, and semicolons.
- Avoid low-information phrases such as not A but B, it is important to note, it is worth noting, and in conclusion.
- Do not use hype words such as groundbreaking, game-changing, robust, or seamless unless the paper itself supports that exact claim.
