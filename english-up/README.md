# Daily up · English up

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](../LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](english-up/scripts/build_tracker.py)
[![Agent Skill](https://img.shields.io/badge/Agent%20Skill-SKILL.md-8A2BE2.svg)](SKILL.md)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#贡献)

> 把「学英语」变成每天自动运转的一套系统：**每日文章推送 → 生词/语法标注讲解 → 作文批改 → 打卡记录 → 周复盘**。
> Turn English learning into a daily automated loop: **article push → annotated explanation → essay correction → tracking → weekly review**.

本目录是 [Daily up](../README.md) 合集库中的**项目 1**，以 Agent Skill 形式交付：**English up**。

---

## 30 秒看懂：它每天给你什么

你每天会收到**一篇文章 + 三个任务 + 一道写作题**，学完把「不会的单词/语法点 + 答案 + 作文」发回去，然后拿到**标注版原文 + 逐条讲解 + 作文批改 + 当日记录**。聊天里只回 5 行，其余全部落进文件：

```
📄 每日记录/2026-10-16_W1D2.md      ← 文章 + 标注版原文 + 讲解 + 批改 + 明日难度调整
✍️ 6/15 → 9/15（+3，刚到及格线）      ← 作文折算分，含"中式表达 6 处 → 2 处"
⚠️ 最致命两条：get ready → get right；逗号不能连接两个句子
✅ 已更新：每日打卡表.xlsx（当日行）· 写作批改记录.md · 指标看板
```

- **文章**：250–300 词原创，按阶段递增难度，文内埋 6 个地道语块
- **标注**：你列出的词/语法点被【1】【2】… 标回原文对应位置，逐条讲用法、例句与常见坑
- **批改三项**：中式表达 → 地道替换（表格）/ 语法搭配硬伤 / 3 个可升级句（你必须自己重写第 2 稿）
- **数据落地**：打卡表 xlsx（自动完成率 + 周汇总 SUMIF）、写作台账、每日记录、周复盘

## 它解决的真实问题

| 常见死法 | English up 的做法 |
|---|---|
| 找不到每天读什么、写什么 | 每天自动出文章 + 题目，难度跟着你的错题走 |
| 只输入不输出，读得多说得烂 | 强制每日输出：口语至少一项、作文至少一项，**「每天有一段出声的英语」是红线** |
| 在图书馆／自习室没法练口语 | **两段式作息**：安静环境做输入与写作，出声与录音挪到回家路上和家里 |
| 不敢开口、抗拒录音 | **开口恐惧阶梯 L1–L6**：对口型跟读 → 耳语 → 30 秒录音 → 每天 3 分钟，达标才升级 |
| 计划做着做着就断了 | 打卡表 + 每日提醒 + 周复盘 + 「零打卡日」禁止规则 |
| AI 长回答烧 token | **文件优先**：内容全写进文件，聊天只给路径 + 结论 + 追问（≤5 行） |

## English

**English up** is a long-horizon English-learning workflow packaged as an agent skill. Each day it produces one original 250–300 word article (difficulty adapts to your mistakes), three tasks, and a writing prompt; you send back the words/grammar you didn't know, your answers, and your essay — it returns the article re-annotated in place, line-by-line explanations, a three-part essay correction (Chinglish → natural / grammar & collocation errors / 3 sentences to upgrade), plus a daily record and updated trackers.

Key ideas: a **two-block schedule** (quiet input at the library, speaking at home/on the way), an **anxiety ladder L1–L6** for speaking, **file-first output** to keep token costs low, and **data-driven difficulty**. See [`SKILL.md`](SKILL.md) and the English prompt in [`references/system-prompt.en.md`](references/system-prompt.en.md).

## 适合谁 / 不适合谁

- ✅ 想长期（数周～一年）系统学英语、有明确考试目标、学习环境不能出声、需要外部反馈的人
- ✅ 想把自己的学习流程做成「可自动运行的 AI 工作流」的人
- ❌ 想要三天速成、只背单词不做输出、不愿动笔写第 2 稿的人

## 目录结构

```
english-up/                        # ← Agent Skill（自包含，可单独拷进技能目录）
├── SKILL.md                       # 技能入口（frontmatter: name / description / license）
├── LICENSE                        # MIT 全文（本目录自包含，可单独取用）
├── references/
│   ├── system-prompt.md           # 通用系统提示词（中文，占位符版）
│   ├── system-prompt.en.md        # English system prompt
│   ├── year-plan-template.md      # 一年计划模板
│   ├── speaking-ladder.md         # 口语开口恐惧阶梯 L1–L6
│   └── writing-log-template.md    # 写作批改台账模板
├── assets/
│   └── daily-record-template.md   # 每日记录模板
└── scripts/
    ├── build_tracker.py           # 打卡表 xlsx 生成器
    └── requirements.txt           # openpyxl
```

> ⚠️ 仓库里**不包含**个人学习记录：`英语提升/`（计划、打卡、作文、录音）已被 `.gitignore` 排除。

## 快速开始

### 1. 安装为 Agent Skill

```bash
# Claude Code
mkdir -p ~/.claude/skills && cp -r english-up ~/.claude/skills/

# 其他客户端：把 english-up/ 放进你的技能目录并按文档注册
```

之后提出「制定一年英语学习计划」「每天推一篇英语文章」「帮我批改作文」「我放不开不敢说英语」这类需求，技能会被自动加载。

### 2. 或者只拿提示词

把 [`references/system-prompt.md`](references/system-prompt.md)（中文）或 [`references/system-prompt.en.md`](references/system-prompt.en.md)（English）的代码块整段发给任意 AI 助手，填掉 `{{占位符}}` 即可开跑。

### 3. 生成打卡表

```bash
pip install openpyxl
# 或：pip install -r english-up/scripts/requirements.txt
python english-up/scripts/build_tracker.py \
  --out 每日打卡表.xlsx \
  --start 2026-10-19 \
  --weeks 52 \
  --prep-days 4 \
  --app 不背单词 \
  --exam-name CET-6 \
  --daily-min 150
```

参数：`--daily-min` 工作日目标分钟；`--sat-min`（默认 210）/`--sun-min`（默认 120）周末目标；`--prep-days` 预备期天数。
生成后建议用 Excel / LibreOffice 打开一次让公式求值。

## 设计原则

| 原则 | 说明 |
|---|---|
| 每天必须有**输出** | 出声口语或作文至少一项，不做「只输入不输出」 |
| 红线的定义要准 | **「每天有一段出声的英语」是红线，「必须录音」不是**——否则一遇阻力就整个板块停摆 |
| 文件优先，聊天只给增量 | 文章/讲解/批改全部写进文件，聊天只回路径 + 结论 + 追问（≤5 行） |
| 难度跟着数据走 | 按前一天的错题类型调整文章难度、句长、语块复现与写作硬性语法要求 |
| 队列不许雪崩 | 背单词待复习 >120 张时当天不加新词 |
| 改稿才算学会 | 批改后必须自己重写第 2 稿，只看批改不复写等于白改 |

## 贡献

欢迎 issue / PR：新增语言模板、改进 `build_tracker.py`、补充阶梯阶段、修错别字都算。提交前请保持「文件优先、聊天 ≤5 行」的设计约定。

## License

MIT © 2026 Aruzestattvat —— 见 [../LICENSE](../LICENSE)（仓库级 MIT；本项目未单独附加条款）。可自由使用、修改、分发与商用，保留版权与许可声明即可。
