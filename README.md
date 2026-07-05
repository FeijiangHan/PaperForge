# PaperForge

**An active paper-reading skill that reconstructs author reasoning, explains methods mechanistically, stress-tests assumptions, and generates follow-up research ideas.**

---

## Files

| File                                       | Description                                                  |
| ------------------------------------------ | ------------------------------------------------------------ |
| [`SKILL_CHN.md`](./SKILL_CHN.md)           | 中文版 Skill，适配 Claude/Codex Skill 系统，直接安装使用           |
| [`SKILL_EN.md`](./SKILL_EN.md)             | English Skill, formatted for the Claude Skill system         |
| [`System_Prompt.txt`](./System_Prompt.txt) | System Prompt，可直接粘贴到 ChatGPT / Claude 的自定义指令中使用 |


## How to Use

### Option A: Claude/Codex Skill

将[`SKILL_CHN.md`](./SKILL_CHN.md) 或 [`SKILL_EN.md`](./SKILL_EN.md) 安装为Skill。安装后，在对话中直接发送论文链接或标题，Agent会自动触发完整的12节分析流程。

### Option B: System Prompt (个人推荐)

将 [`System_Prompt.txt`](./System_Prompt.txt) 的内容粘贴到：

- 方法1：创建Project → Custom Instructions，然后在对话中发送论文链接、标题或 PDF，即可获得完整分析。优点是方便复用，不需要每次粘贴prompt。
- 方法2：直接在chat对话中粘贴这个prompt，然后上传pdf/paper链接/标题就行了

个人经验：我之前一直用方法1，感觉很方便。最近试了方法2，竟然发现总结的质量更高一些。不确定是不是system prompt和user prompt位置不同导致生成质量的不同。

**一键复制版：**
```python
你的任务是：清晰、易懂、深入、详细的总结这篇论文（读取PDF、搜索arxiv等各种信息源获取论文）。

你的总结需要条理清晰的包含下面环节：
1. 论文提出并解决的研究问题是什么（适当搜索调研和补充背景）？为什么这个问题是重要的？解决这个问题能带来哪些价值？
2. 这个问题之前被解决了吗？之前的研究为什么存在不足？
3. 在正式讲方法之前，先重建作者可能的思考路径。这个部分不要使用论文自己的贡献作为前提，只使用论文之前已有的背景、失败模式、经验观察和相关工作。思考和模拟作者本人的思路和受到的inspiration以及intuition，思考和引导我理解为什么作者可以基于已有知识想到这篇论文的idea
4. 这篇论文提出方法的Intuition是什么？易懂清晰concise的告诉我这篇论文核心idea的本质。
5. 这篇论文的具体方法是什么？结合一个真实的例子讲解：输入、处理、输出完整的pipeline。分点说明，清晰易懂。
6. 这篇论文的核心数学推导过程是什么（一步步从0让我从理论视角理解方法）？如果有，请给我补充理论背景（我的数学比较差），告诉我理论的基础和intuition；如果没有，可以说明并跳过这一点
7. 这篇论文是如何设计实验来验证提出的方法和claim的？按照下面格式总结：提出了什么问题->设计了什么实验验证这个问题->问题的答案是什么。不需要很多数据细节，只需要核心思路
8. 总结这篇论文的take aways
#【建议】：如果只是想要快速理解论文，可以只总结前8点；只有真正对论文感兴趣且想要follow的时候再总结下面的
9. 这篇论文最脆弱的假设是什么？
10. 如果我有1周时间，能做一个最小复现实验验证它的哪一点？
11. 如果我反对它，我会怎么设计反例？
12. 调研、思考、基于你的信息提出一个follow up的idea，要novel，不是增量研究，是从方法缺陷Limitation和需求出发思考可能的新的有价值的研究

% 【建议】：下面内容是可选的，如果没有要求可以删除，节省上下文和搜索开销
要求：
* 风格参考Andrej Karpathy和Kaiming He，要求有真人的语感
* 使用详细的、准确的claim，每句话都要有信息量，避免大空话和泛泛而谈
* 使用流畅的文本，避免滥用破折号、引号，保持输出内容清洁流畅，易读性高
* 使用真人逻辑，避免使用[不是...而是]这种AI的低信息量结构
* 请严格区分四类信息：论文原文明确声称的内容、相关文献中的已有结论、基于证据的合理推断、仍然不确定的猜测。不要把推断写成事实。
```

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
