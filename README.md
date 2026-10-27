# 鹈鹕骑士 · 海岸生存

更新日期：2026-10-27  
项目所有者：ScarfQian  
整理与开发记录：Codex

一只骑自行车的鹈鹕，在海岸上收集珍珠、选择升级并抵御敌潮的俯视角生存肉鸽游戏。使用原生 HTML、CSS、JavaScript 与 SVG；当前所有运行内容均内嵌在单个 HTML 中，无构建流程或外部资源依赖。

## 唯一工作目录与当前入口

`/Users/qianweijin/Library/Mobile Documents/com~apple~CloudDocs/10-开发/2-Game/1-鹈鹕骑士`

后续开发、版本快照、修改记录和交接均在本目录进行。旧 Codex 可视化目录不再作为开发入口。

| 项目 | 当前值 |
| --- | --- |
| 当前版本 | 0.1.1 |
| 版本身份 | 开发原型，首次在线发布配置 |
| 唯一可编辑游戏入口 | [index.html](index.html) |
| 当前版本登记 | [version.json](version.json) |
| 初始游戏快照 | [versions/v0.1.0/index.html](versions/v0.1.0/index.html) |
| 当前游戏快照 | [versions/v0.1.1/index.html](versions/v0.1.1/index.html) |
| 版本变更记录 | [CHANGELOG.md](CHANGELOG.md) |
| 开发日志 | [docs/DEVELOPMENT.md](docs/DEVELOPMENT.md) |
| 新对话交接说明 | [docs/HANDOFF.md](docs/HANDOFF.md) |

当前版本以 `version.json` 为准。它将运行入口、对应快照和修改记录关联起来；历史快照仅用于追溯和恢复，不独立开发。

## GitHub 与在线开发

- 代码仓库：[ScarfQian/pelican-knight](https://github.com/ScarfQian/pelican-knight)。
- 在线游戏：[鹈鹕骑士 · 海岸生存](https://scarfqian.github.io/pelican-knight/)，首次部署已完成。
- `main` 保存已获用户同意发布的内容，GitHub Pages 从 `main` 根目录发布；`.nojekyll` 使 HTML 按静态文件提供。
- 后续每项维护先在本目录创建独立分支，例如 `feat/new-weapon` 或 `fix/pause-controls`；完成版本、快照与日志后，按用户指令提交并推送分支，创建 Pull Request（PR）。
- PR 说明实际改动、行为变化和已完成的核对。用户明确决定合并后，才能合并到 `main` 并更新在线版；不自动合并、不直接向 `main` 推送维护改动。
- `main` 的保护规则要求通过 PR 修改，管理员同样受约束；禁止强推和删除。不设置其他账号必须批准的门槛，合并决定由用户给出。
- 本次首次上传是建立 `main` 的初始发布。后续合并使用 PR；不要求额外账号审批，也不自动开展游戏测试。

GitHub 用于代码、差异审阅和发布；开发入口仍是本目录的 `index.html`。玩家纪录仍按浏览器来源保存在本地，`file://` 与在线站点的纪录不会自动互通。

## 启动与操作

直接用现代浏览器打开 [index.html](index.html)，点击“出发，抢回海岸”。

- WASD 或方向键移动，自动瞄准并发射小鱼。
- 空格或屏幕冲刺按钮：短暂无敌冲刺。
- 收集珍珠升级，每次随机选择三项本领之一；可用数字键 1 / 2 / 3。
- P 或 Esc 暂停；支持继续与重新开始。
- 触屏设备提供虚拟摇杆与冲刺按钮。
- 右上角可开启音效，默认关闭。
- 坚持 180 秒并击败首领获胜。首领在第 135 秒登场；时间到达后若首领尚存，继续战斗直至胜负确定。

如需要本地 HTTP 预览，可在本目录运行：

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

然后打开 `http://127.0.0.1:8000/`。此命令仅为可选预览方式，本次未运行。

## 目录职责

```text
1-鹈鹕骑士/
├── index.html                         # 当前开发与运行入口
├── version.json                       # 当前版本、快照、最近修改编号
├── README.md                          # 项目入口与使用说明
├── AGENTS.md                          # 本项目的开发与记录约定
├── .gitignore                         # 忽略 macOS 目录元数据
├── .nojekyll                          # GitHub Pages 直接发布静态文件
├── CHANGELOG.md                       # 按版本说明变化
├── docs/
│   ├── DEVELOPMENT.md                 # 修改原因、实现位置、核对情况
│   └── HANDOFF.md                     # 新对话直接接手所需信息
└── versions/
    ├── v0.1.0/
    │   └── index.html                 # 初始肉鸽游戏快照
    ├── v0.1.1/
    │   └── index.html                 # 首次在线发布快照，游戏内容未变
    └── prototype/
        └── 261026-pelican-ride.html    # 最早的骑行动画，历史原型
```

## 版本与修改追溯

当前采用 Git 分支与 PR、完整版本快照和文本日志管理。每批完成的修改应做到：

1. 从 `version.json` 确认当前版本，仅在 `index.html` 修改当前游戏。
2. 为修改分配唯一编号，如 `20261027-002`，在开发日志记录需求、原因、涉及文件和行为变化。
3. 完成后增加版本号，并将当时的游戏保存为新的 `versions/vX.Y.Z/index.html`；既有快照保持原样。
4. 同步更新 `version.json`、`CHANGELOG.md`、`docs/DEVELOPMENT.md`；若入口、结构或待办发生变化，更新交接说明。
5. 当前入口应与该版本登记的快照一致。未完成的工作在开发日志说明，不登记为已完成版本。

版本号约定：修复及小幅表现调整增加 PATCH；新玩法或较完整功能增加 MINOR；不兼容的项目结构或存档协议变化增加 MAJOR。原始单文件方案无需为版本管理引入构建工具。

## 当前核对范围

初始迁移核对了原内容保持、游戏快照、版本登记及文档相对链接。0.1.1 首次发布核对了 Pages 部署成功、在线 HTTP 200，以及线上 HTML 与当前入口一致。没有运行自动化测试、浏览器试玩、移动端实测或性能测试；功能列表来自当前实现，发布成功不代表这些体验已被验证。

最佳击退数、最长时间和胜利次数保存在浏览器的 `localStorage`，键为 `pelican-coast-best-v1`。这些浏览器存档不在项目目录内，本次没有读取或迁移浏览器存档。
