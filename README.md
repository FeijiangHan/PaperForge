# PaperForge

**An active paper-reading skill that reconstructs author reasoning, explains methods mechanistically, stress-tests assumptions, and generates follow-up research ideas.**

---

## Files

| File                                       | Description                                                  |
| ------------------------------------------ | ------------------------------------------------------------ |
| [`SKILL_CHN.md`](./SKILL_CHN.md)           | 中文版 Skill，适配 Claude Skill 系统，直接安装使用           |
| [`SKILL_EN.md`](./SKILL_EN.md)             | English Skill, formatted for the Claude Skill system         |
| [`System_Prompt.txt`](./System_Prompt.txt) | System Prompt，可直接粘贴到 ChatGPT / Claude 的自定义指令中使用 |


## How to Use

### Option A: Claude Skill（推荐）

将 [`SKILL_CHN.md`](./SKILL_CHN.md) 或 [`SKILL_EN.md`](./SKILL_EN.md) 安装为 Claude Skill。安装后，在对话中直接发送论文链接或标题，Claude 会自动触发完整的12节分析流程。

### Option B: System Prompt（GPT / Claude 通用）

将 [`System_Prompt.txt`](./System_Prompt.txt) 的内容粘贴到：

- **ChatGPT**：创建Project → Custom Instructions
- **Claude**：Project Instructions

然后在对话中发送论文链接、标题或 PDF，即可获得完整分析。

小红书帖子【用AI读论文两年半，我认为最好用的prompt - 幸运降临中】

https://www.xiaohongshu.com/discovery/item/6a300c2e00000000060363b6?source=webshare&xhsshare=pc_web&xsec_token=ABYfMQEP9MGgfWyKvWBWs6xOMpOBKCFU80meDyRtv5h5A=&xsec_source=pc_share

### 如何定制人文社科的论文阅读prompt

刚才试了试感觉GPT给的修改版本看起来挺好的，
就是我没做过文科research不知道行不行。
大家可以试试，直接复制给GPT下面的内容，打开联网搜索和Reasoning功能。

“https://github.com/FeijiangHan/PaperForge
帮我调研文科社科论文（+具体方向）阅读和理工科的差异，思考如何修改这个GitHub中的skills使其更适合文科社科（+具体方向），保留核心精华（如反推思路）”