🌐 语言: **中文** | [English](README.md)

# GitHub 贡献图模拟器

https://github.com/kyshipit/gh-heatmap-generator#github-contribution-graph-simulator

一个用于学习和可视化模拟 GitHub 贡献图的、教育性开源 Web 工具。

## ⚠️ 免责声明

[https://github.com/kyshipit/gh-heatmap-generator#%EF%B8%8F-disclaimer](https://github.com/kyshipit/gh-heatmap-generator#️-disclaimer)

本项目仅用于教育和研究目的。

本工具的主要目标是帮助开发者理解 GitHub 计算和显示贡献热力图（例如如何处理 AuthorDate、CommitDate、时区和空提交）的底层机制。

我们不鼓励也不支持使用本工具伪造虚假简历、误导雇主或人为夸大开发者的声誉。

使用本工具即表示你同意：你对自己的使用行为承担全部责任。我们公开邀请 GitHub 安全与工程团队审查本项目，并在其认为必要时修补其贡献计算逻辑中的任何底层漏洞。

## 📖 背景：为什么伪造提交会失败？

https://github.com/kyshipit/gh-heatmap-generator#-background-why-do-fake-commits-fail

许多开发者尝试使用类似 `git commit --date="..."` 的简单脚本来生成虚假的贡献图。然而，这些提交通常无法在他人可见的公开贡献图上显示。本工具针对三个主要失败点进行处理：

- **空提交（`--allow-empty`）**：GitHub 的公共 API 会积极过滤掉零文件差异的提交。
- **时区偏移**：指定日期时不带时间（或默认使用 `00:00:00`）可能会因 UTC 偏移计算而把贡献块移到前一天或后一天。
- **双时间戳**：Git 同时维护 AuthorDate 和 CommitDate。如果二者不同步，GitHub 的公共缓存系统可能会忽略历史日期。

## 🛠️ 功能

[https://github.com/kyshipit/gh-heatmap-generator#%EF%B8%8F-features](https://github.com/kyshipit/gh-heatmap-generator#️-features)

- **可视化界面**：点击 7x53 网格来绘制你的贡献图。
- **准确的月份对齐**：实时渲染与周次完美对齐的月份标签。
- **智能脚本生成**：使用 Bash 函数和 for 循环生成优化后的 Bash 脚本，使脚本保持简洁。
- **时区安全**：在生成的日期中硬编码 `T12:00:00`，以绕过 UTC 边界问题。
- **真实差异**：生成会修改占位文件 `activity.txt` 的脚本，以确保提交被视为“真实”贡献。

## 🚀 如何使用

https://github.com/kyshipit/gh-heatmap-generator#-how-to-use

1. 克隆本仓库或下载源文件（`index.html`、`style.css`、`app.js`）。

2. 在任意现代 Web 浏览器中打开 `index.html`（无需本地服务器或 Node.js）。

3. 选择目标年份，点击网格以选择日期和提交强度（0 到 4）。

4. 点击“Generate Git Commit Commands”。

5. 从输出框中复制生成的 Bash 脚本。

6. 在本地 Git 仓库中创建一个名为 `script.sh` 的新文件，粘贴复制的代码并保存。

7. 在本地 Git 终端中运行该脚本：

```bash
bash script.sh
git push origin main
```

## 🤝 贡献

https://github.com/kyshipit/gh-heatmap-generator#-contributing

欢迎贡献、提交 Issue 和功能请求！如果你发现 bug 或有改进该工具的想法，欢迎随时提交 Issue 或 Pull Request。

## 📄 许可证

https://github.com/kyshipit/gh-heatmap-generator#-license

本项目采用 https://choosealicense.com/licenses/mit/ 许可证授权。