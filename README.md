# Daily up

> 把「学英语」变成每天自动运转的一套系统：**每日文章推送 → 生词/语法标注讲解 → 作文批改 → 打卡记录 → 周复盘**。
> 本仓库包含一个可直接安装的 Agent Skill：**English up**（`english-up/`）。

## 这是什么

一套面向长期（数周～一年）英语学习的工作流，不只是一张计划表：

- **每日原创文章**：250–300 词，按阶段递增难度，文内埋 6 个地道语块
- **标注式讲解**：把你不会的单词/语法点标回原文对应位置，逐条解释用法与常见坑
- **作文批改三项**：中式表达 → 地道替换 / 语法搭配硬伤 / 3 个可升级句（自己重写第 2 稿）
- **两段式作息**：安静环境做输入与写作，出声与录音放家里/路上——解决「在图书馆没法练口语」
- **口语开口恐惧阶梯 L1–L6**：从对口型跟读、耳语，到 30 秒录音，最后每天 3 分钟
- **数据落地**：打卡表 xlsx（自动完成率 + 周汇总 SUMIF）、写作台账、每日记录、周复盘
- **动态难度调节**：按你的每日表现自动升降文章难度、复现错过的语块

## 目录结构

```
Daily up/
├── README.md
├── LICENSE
├── .gitignore
└── english-up/                    # ← Agent Skill
    ├── SKILL.md                   # 技能入口（frontmatter: name / description）
    ├── references/
    │   ├── system-prompt.md       # 通用系统提示词（占位符版，可直接交付给其他 AI）
    │   ├── year-plan-template.md  # 一年计划模板
    │   ├── speaking-ladder.md     # 口语开口恐惧阶梯 L1–L6
    │   └── writing-log-template.md# 写作批改台账模板
    ├── assets/
    │   └── daily-record-template.md  # 每日记录模板
    └── scripts/
        └── build_tracker.py       # 每日打卡表 xlsx 生成器（openpyxl）
```

> ⚠️ 仓库里**不包含**个人学习记录：`英语提升/`（计划、打卡、作文、录音）已被 `.gitignore` 排除。

## 快速开始

### 1. 安装为 Agent Skill

把 `english-up/` 整个目录复制到你的 agent 技能目录：

```bash
# DSH：放进你的用户技能目录后按客户端文档注册
# Claude Code：
mkdir -p ~/.claude/skills
cp -r english-up ~/.claude/skills/
```

之后当你提出「制定一年英语学习计划」「每天推一篇英语文章」「帮我批改作文」「我放不开不敢说英语」这类需求时，技能会被自动加载。

### 2. 或者只拿提示词

把 [`english-up/references/system-prompt.md`](english-up/references/system-prompt.md) 的代码块整段发给任意 AI 助手，填掉 `{{占位符}}` 即可开跑。

### 3. 生成打卡表

```bash
python english-up/scripts/build_tracker.py \
  --out 每日打卡表.xlsx \
  --start 2026-10-19 \
  --weeks 52 \
  --prep-days 4 \
  --app 不背单词 \
  --exam-name CET-6 \
  --daily-min 150
```

参数：`--daily-min` 工作日目标，`--sat-min`（默认 210）/`--sun-min`（默认 120）周末目标，`--prep-days` 预备期天数。
只依赖 `openpyxl`，生成后建议用 Excel/LibreOffice 打开一次让公式求值。

## 设计原则

| 原则 | 说明 |
|---|---|
| 每天必须有**输出** | 出声口语或作文至少一项，不做「只输入不输出」 |
| 红线的定义要准 | **「每天有一段出声的英语」是红线，「必须录音」不是**——否则一遇阻力就整个板块停摆 |
| 文件优先，聊天只给增量 | 文章/讲解/批改全部写进文件，聊天只回路径 + 结论 + 追问（≤5 行），长期运行才省 token |
| 难度跟着数据走 | 每天根据前一天的错题类型调整文章难度、句长与语块复现 |
| 队列不许雪崩 | 背单词待复习 >120 张时当天不加新词 |
| 改稿才算学会 | 批改后必须自己重写第 2 稿 |

## 发布到 GitHub

```bash
git init -b main
git add .
git commit -m "feat: English up skill — 一年制英语学习系统"
git remote add origin git@github.com:<你的用户名>/Daily-up.git
git push -u origin main
```

> 仓库名建议用 `Daily-up` 或 `daily-up`（GitHub 仓库名含空格会被转成 `-`）。

## License

MIT © 2026 Aruzestattvat —— 见 [LICENSE](LICENSE)。可自由使用、修改、分发与商用，保留版权与许可声明即可。
