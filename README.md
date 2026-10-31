# PaperForge

[简体中文](./README.md) | [English](./README_EN.md)

**An active paper-reading skill that reconstructs author reasoning, explains methods mechanistically, stress-tests assumptions, and generates follow-up research ideas.**

---

## Files

| File | Description |
| --- | --- |
| [Chinese Skill](./.agents/skills/paper-reading-zh/SKILL.md) | 中文版Agent Skills |
| [English Skill](./.agents/skills/paper-reading/SKILL.md) | English version Agent Skills |
| [System_Prompt.txt](./System_Prompt.txt) | 中文版Prompt |
| [System_Prompt_EN.txt](./System_Prompt_EN.txt) | English version Prompt |

## How to Use

### Option A: Claude/Codex Skill

安装 [.agents/skills/paper-reading-zh/SKILL.md](./.agents/skills/paper-reading-zh/SKILL.md)（中文）或 [.agents/skills/paper-reading/SKILL.md](./.agents/skills/paper-reading/SKILL.md)（English），并放在对应的 Skill 目录中。

### Option B: System Prompt (个人推荐)

感觉ChatGPT的chat模式总结论文比codex更好（codex/cc已经不说人话），所以有日常读需求的话，我建议使用网页版chat模式总结论文

将 [`System_Prompt.txt`](./System_Prompt.txt) 的内容粘贴到：

- 方法1：创建Project → Custom Instructions，然后在对话中发送论文链接、标题或 PDF，即可获得完整分析。优点是方便复用，不需要每次粘贴prompt。
- 方法2：直接在chat对话中粘贴这个prompt，然后上传pdf/paper链接/标题就行了

个人经验：我之前一直用方法1，感觉很方便。最近试了方法2，竟然发现总结的质量更高一些。不确定是不是system prompt和user prompt位置不同导致生成质量的不同。

**一键复制版（concise版本）：**
```txt
你的任务是：清晰、易懂、深入、详细的总结这篇论文（读取PDF、搜索arxiv等各种信息源获取论文）。

你的总结需要条理清晰的包含下面环节：
1. 论文提出并解决的研究问题是什么（适当搜索调研和补充背景）？为什么这个问题是重要的？解决这个问题能带来哪些价值？
2. 这个问题之前被解决了吗？之前的研究为什么存在不足？
3. 在正式讲方法之前，先重建作者可能的思考路径。这个部分不要使用论文自己的贡献作为前提，只使用论文之前已有的背景、失败模式、经验观察和相关工作。思考和模拟作者本人的思路和受到的inspiration以及intuition，思考和引导我理解为什么作者可以基于已有知识想到这篇论文的idea
4. 这篇论文提出方法的Intuition是什么？易懂清晰concise的告诉我这篇论文核心idea的本质。
5. 这篇论文的具体方法是什么？结合一个真实的例子讲解：输入、处理、输出完整的pipeline。分点说明，清晰易懂。
6. 这篇论文是如何设计实验来验证提出的方法和claim的？按照下面格式总结：提出了什么问题->设计了什么实验验证这个问题->问题的答案是什么。不需要很多数据细节，只需要核心思路
7. 总结这篇论文的take aways
8. 这篇论文最脆弱的假设是什么？
9. 调用搜索工具，调研这篇论文的后续研究，是否有进一步的扩展或者反驳，以及新的认知？

要求：
* 风格参考Andrej Karpathy和Kaiming He，要求有真人的语感
* 使用详细的、准确的claim，每句话都要有信息量，避免大空话和泛泛而谈
* 可以结合可视化讲解复杂概念
```

**一键复制版（完整版本）：**
```txt
你的任务是：清晰、易懂、深入、详细的总结这篇论文（读取PDF、搜索arxiv等各种信息源获取论文）。

你的总结需要条理清晰的包含下面环节：
1. 论文提出并解决的研究问题是什么（适当搜索调研和补充背景）？为什么这个问题是重要的？解决这个问题能带来哪些价值？
2. 这个问题之前被解决了吗？之前的研究为什么存在不足？
3. 在正式讲方法之前，先重建作者可能的思考路径。这个部分不要使用论文自己的贡献作为前提，只使用论文之前已有的背景、失败模式、经验观察和相关工作。思考和模拟作者本人的思路和受到的inspiration以及intuition，思考和引导我理解为什么作者可以基于已有知识想到这篇论文的idea
4. 这篇论文提出方法的Intuition是什么？易懂清晰concise的告诉我这篇论文核心idea的本质。
5. 这篇论文的具体方法是什么？结合一个真实的例子讲解：输入、处理、输出完整的pipeline。分点说明，清晰易懂。
6. 这篇论文的核心数学推导过程是什么（一步步从0让我从理论视角理解方法）？如果有，请给我补充理论背景（我的数学比较差），告诉我理论的基础和intuition；如果没有，可以说明并跳过这一点。所有数学公式使用准确的markdown语法确保渲染成功。
7. 这篇论文是如何设计实验来验证提出的方法和claim的？按照下面格式总结：提出了什么问题->设计了什么实验验证这个问题->问题的答案是什么。不需要很多数据细节，只需要核心思路
8. 总结这篇论文的take aways
9. 这篇论文最脆弱的假设是什么？
10. 如果我有1周时间，能做一个最小复现实验验证它的哪一点？
11. 如果我反对它，我会怎么设计反例？
12. 调用搜索工具，调研这篇论文的后续研究，是否有进一步的扩展或者反驳，以及新的认知？
13. 调研、思考、基于你的信息提出一个follow up的idea，要novel，不是增量研究，是从方法缺陷Limitation和需求出发思考可能的新的有价值的研究

要求：
* 风格参考Andrej Karpathy和Kaiming He，要求有真人的语感
* 使用详细的、准确的claim，每句话都要有信息量，避免大空话和泛泛而谈
* 使用流畅的文本，避免滥用破折号、引号，保持输出内容清洁流畅，易读性高
* 使用真人逻辑，避免使用[不是...而是]这种AI的低信息量结构
* 可以结合可视化讲解复杂概念
* 请严格区分四类信息：论文原文明确声称的内容、相关文献中的已有结论、基于证据的合理推断、仍然不确定的猜测。不要把推断写成事实。
```

**建议：**：

1. 用之前的prompt总结会导致失去视觉理解，例如某些论文的figure 1和实验画图挺好看的，可以帮我们积累审美，还能帮我们更好的理解论文。
所以可以试试生成html+交互，也可以试试用 claude opus 5.5一键生成论文讲解可视化视频
	
2. 之前的prompt对每篇论文都生成一大段，但是我们有时候发现对某篇论文其实不太感兴趣，没有阅读动力。
现在可以最开始加一个环节，让LLMs基于论文给我们提出1-2个research questions，我们先看看对这个问题感不感兴趣，不感兴趣直接跳过；感兴趣就可以带着解决动问题的动力更好的读论文
	
3. 安装chatgpt浏览器插件，这样打开一个blog/论文可以直接右侧chat总结，无需拷贝论文链接再发给chat


### Option C: 自我进化

如果你已经有自己的论文阅读prompt或skills，可以让Agent / LLM自动review这个repo，并结合你原来的版本取长补短。

你可以让模型完成三件事：

1. 比较你现有prompt和PaperForge的差异
2. 保留你原来workflow中最适合自己的部分
3. 合并出一版更贴合你研究方向和阅读习惯的论文阅读prompt

我认为需要注意的是"§ 3 — 重建作者的思考路径"和"§ 9 — 最脆弱的假设","§ 10 — 最小复现实验","§ 11 — 最强反例设计"

PaperForge也可以作为你自己paper-reading workflow的起点。

### Option D: 定制人文社科等其他方向的论文阅读prompt

目前的版本主要侧重理工科等重实验和方法论的论文阅读。
如果你想改成适合文科社科的版本，可以试试直接复制给GPT下面的内容，打开联网搜索和Reasoning功能。

> https://github.com/FeijiangHan/PaperForge
> 帮我调研文科社科论文（具体方向）阅读和理工科论文阅读的差异，并思考如何修改这个GitHub repo中的skills，使其更适合文科社科（具体方向）。请保留核心精华，例如反推作者思路、拆解论证结构、识别关键假设、寻找可延展的问题。


你可以把其中的 具体方向 替换成：
* history
* sociology
* political science
* philosophy
* anthropology
* education
* communication
* economics
* law
* literary studies

---

## Reference

小红书帖子【用AI读论文两年半，我认为最好用的prompt - 幸运降临中】

https://www.xiaohongshu.com/discovery/item/6a300c2e00000000060363b6?source=webshare&xhsshare=pc_web&xsec_token=ABYfMQEP9MGgfWyKvWBWs6xOMpOBKCFU80meDyRtv5h5A=&xsec_source=pc_share
