<div align="center">

# L4N Releases

**L4N 发行版归档 · 版本备份 · 一键部署分发源**

为 Left 4 Dead 2 的 L4N 客户端补丁提供发行文件备份，方便部署工具获取与安装。

[下载最新版](https://github.com/STC214/l4n-releases/releases/latest) · [历史版本](https://github.com/STC214/l4n-releases/releases) · [完整说明](readme_l4n.txt)

[作者 B 站](https://space.bilibili.com/644686972) · [原作者网盘](https://pan.baidu.com/s/5Sr2hIwOr_4w8desMhTvNxQ) · [Steam 创意工坊](https://steamcommunity.com/sharedfiles/filedetails/?id=3558049615)

</div>

---

## 关于本仓库

本仓库用于 **L4N 发行版文件的备份与分发**，为一键部署程序提供统一的获取入口，并非 L4N 源码仓库或官方开发仓库。

- **版本备份**：保存发行文件，方便后续管理与取用。
- **部署调用**：保留发行文件的相对目录结构，便于部署工具复制到游戏目录。
- **文档索引**：保留原版使用说明、配置说明与更新日志。

> L4N 由原作者开发与维护。本仓库仅作发行文件归档；如果觉得好用，请通过上方链接关注并支持原作者。

## 获取与安装

1. 打开 [最新版](https://github.com/STC214/l4n-releases/releases/latest) 或 [历史版本](https://github.com/STC214/l4n-releases/releases)，在对应版本的 **Assets** 中下载 `L4N_v*.7z` 或 `.zip` 压缩包并解压；也可通过上方原作者发布渠道获取。
2. 关闭游戏，备份游戏目录中即将被覆盖的同名文件及个人配置。
3. 将发行文件按原有目录结构复制到 **Left 4 Dead 2 游戏根目录**，确认后覆盖同名文件。
4. 详细安装方式、功能配置、兼容性说明与更新日志，请阅读 [原版文档 `readme_l4n.txt`](readme_l4n.txt)。

> **使用提醒**：原版文档说明 L4N 使用内存补丁技术，使用时需自行评估风险；启动项 `-insecure` 可避免进入启用 VAC 的服务器。安装前请完整阅读原版说明。

> **下载时请选原始发行包**：GitHub 自动生成的 `Source code (zip)` 和 `Source code (tar.gz)` 是仓库文件快照，不是对应版本的原始发行包。各版本的使用说明应优先查看压缩包内附带的文档。

## 版本归档与命名

截至本次整理，已归档 **184 个版本**，覆盖 **0.4.1 ～ 2.56.2**；当前最新归档版本为 **2.56.2**。后续版本以 [Releases 页面](https://github.com/STC214/l4n-releases/releases) 为准。

每个版本对应一个 Release，并附带原始压缩包。为使版本列表排序符合预期，**Release 标签与标题中的次版本号统一至少保留两位**：对于 `a.y.z`，仅当 `y` 为一位数字时在前面补 `0`，其余部分保持不变。

| 原始版本 | Release 标签与标题 | 原始附件名 |
| :--- | :--- | :--- |
| `0.4.1` | `L4N_v0.04.1` | `L4N_v0.4.1.7z` |
| `1.5.2` | `L4N_v1.05.2` | `L4N_v1.5.2.zip` |
| `2.8.3` | `L4N_v2.08.3` | `L4N_v2.8.3.7z` |
| `2.56.2` | `L4N_v2.56.2` | `L4N_v2.56.2.7z` |

- **仅规范标签与标题**：原始附件名称、格式与内容均保持不变，描述留空。
- **标签不等于附件名**：接入部署工具时，请读取 Release 的 Assets，避免直接将标签拼接为压缩包名称。
- **Latest 为最新归档版本**：获取最新版本时使用 Latest 入口，不依赖列表第一项。
- **提交记录不代表原作者源码历史**：部分版本使用独立空提交承载发行标签，不包含源码变更。

## 目录导航

| 路径 | 内容 |
| :--- | :--- |
| `bin/` | L4N 相关模块与配套工具 |
| `left4dead2/` | 游戏侧资源、模块与着色器文件 |
| `reshade-shaders/` | 随包提供的 ReShade 着色器资源 |
| `left4dead2.exe` | 随包提供的启动程序 |
| `to_l4n_survivor.exe` | L4N Survivor 转换工具 |
| [`readme_l4n.txt`](readme_l4n.txt) | 原版说明与历史更新日志 |

本地 `l4n/` 目录（含 `old/`）已通过 `.gitignore` 排除；其中的原始压缩包作为 Release 附件分发，不纳入 Git 文件历史。仓库根目录的文件也不代表每个历史版本，请按需下载对应 Release 附件。

## 部署工具接入

- 最新版本元数据：[`GET /repos/STC214/l4n-releases/releases/latest`](https://api.github.com/repos/STC214/l4n-releases/releases/latest)。
- 固定版本元数据：例如 [`GET /repos/STC214/l4n-releases/releases/tags/L4N_v2.08.3`](https://api.github.com/repos/STC214/l4n-releases/releases/tags/L4N_v2.08.3)。
- 从返回结果的 `assets` 中选择原始发行包，通过其 `browser_download_url` 下载；`name` 为真实附件名。
- 固定版本应使用补零后的 Release 标签定位，而非仓库源码快照或空提交内容。
- 解压后按发行文件的相对路径部署，避免打乱目录层级。
- 部署前备份同名文件，保留失败回滚与版本切换的能力。
- 配置项与功能行为以该版本附带的原版文档为准。

## 反馈与致谢

发行文件缺失、仓库说明或部署适配问题，可在本仓库提交 Issue；L4N 本体的功能问题，请先阅读原版文档，再通过原作者公开渠道反馈。

**感谢 L4N 原作者的开发与维护，也感谢社区的分享与支持。**

本仓库不改变原作品及随包第三方组件的权利归属与使用条款；相关说明以原作者及对应组件的声明为准。
