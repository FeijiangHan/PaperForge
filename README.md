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

## 补充：读什么论文？（限AI方向）

AI时代，要用社区共识发现每个月最值得关注的论文，而不是只靠顶会的"免费苦力"审稿人来筛选论文。
我爬了hugging face和alphaxiv榜单，用upvotes-likes-github stars作为筛选指标，过滤-聚合-排序每月互联网热度最大的AI papers，可以直接把这里最终merged的csv丢给你的claude/gpt来个性化分析每月趋势，并提取感兴趣的insights：
https://github.com/FeijiangHan/AI-hot-paper-insights-summary

亲测：这样做，效果比给gpt/claude提供链接再爬取html分析更全面准确

---

## Reference

小红书帖子【用AI读论文两年半，我认为最好用的prompt - 幸运降临中】

https://www.xiaohongshu.com/discovery/item/6a300c2e00000000060363b6?source=webshare&xhsshare=pc_web&xsec_token=ABYfMQEP9MGgfWyKvWBWs6xOMpOBKCFU80meDyRtv5h5A=&xsec_source=pc_share
