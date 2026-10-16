# Daily up

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Projects](https://img.shields.io/badge/projects-3-blue.svg)](#daily-up)
[![English up](https://img.shields.io/badge/English%20up-available-brightgreen.svg)](english-up/SKILL.md)

个人小工具合集。每个子目录都是独立项目，可单独取用。

| 项目 | 一句话 | 状态 | 入口 |
|---|---|---|---|
| [english-up](english-up/) | 一年制英语学习工作流（Agent Skill） | ✅ 可用 | [SKILL.md](english-up/SKILL.md) |
| [focus-search](focus-search/) | 聚焦搜索工具 | 🚧 开发中 | — |
| [WordAbove](https://github.com/Aruzestattvat/WordAbove) | macOS Spotlight 英汉词典「词在上」（已独立成仓） | ✅ 可用 | [README](https://github.com/Aruzestattvat/WordAbove#readme) |

## 约定

- 每个项目自包含：自己的 README、依赖与许可证说明
- 项目之间不共享代码；某个项目长大后会被拆成独立仓库（保留提交历史）
- 单个项目做大后：`git subtree split -P <dir> -b <dir>-standalone` 抽带历史的分支
- 子项目目录**禁止** `git init`（避免嵌套仓库）
- 目录名一律用英文小写；中文名只写在本表格的「一句话」里

## 说明：focus-search 与 WordAbove 的关系

本仓库原本预留的第二个项目叫 `focus-search`。实际开发完成的项目是
**WordAbove（词在上）**——一个 macOS Spotlight 英汉词典，已独立为
[独立仓库](https://github.com/Aruzestattvat/WordAbove)（保留完整提交历史）。

`focus-search/` 目录保留为占位，用于承载后续的聚焦搜索工具；若决定不再做，删掉该目录并移除本表格对应行即可。

## License

MIT © 2026 Aruzestattvat（各项目如有特殊许可，以项目内说明为准）
