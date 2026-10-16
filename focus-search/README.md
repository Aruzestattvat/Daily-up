# focus-search（占位）

聚焦搜索工具 —— **尚未开发**，本目录暂时只是占位。

## 背景

Daily up 原本规划第二个项目为 `focus-search`。实际完成的第二个项目是
**WordAbove（词在上）**——macOS Spotlight 英汉词典，已独立为
[Aruzestattvat/WordAbove](https://github.com/Aruzestattvat/WordAbove)（保留完整提交历史）。

本目录保留给后续可能的「聚焦搜索」工具。如果决定不再做，删除本目录并在根
[README](../README.md) 的表格中移除对应行即可。

## 若要在此落地

按合集库约定：

- 本项目**自包含**：自己的 `README.md`、依赖清单与许可说明
- 目录名用英文小写；中文名写在根 README 的表格里
- **禁止**在此目录内 `git init`（会产生嵌套仓库）
- 项目之间零共享代码；长大后用 `git subtree split -P focus-search -b focus-search-standalone` 抽离
