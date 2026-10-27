# 鹈鹕骑士：项目开发约定

日期：2026-10-27  
项目所有者：ScarfQian  
记录：Codex

## 工作范围

唯一工作目录为：

`/Users/qianweijin/Library/Mobile Documents/com~apple~CloudDocs/10-开发/2-Game/1-鹈鹕骑士`

本项目与研究论文工作区独立。不要在旧 Codex 可视化目录、论文目录或历史快照中继续开发游戏。

开始工作时阅读 `README.md`、`version.json` 和 `docs/HANDOFF.md`；需要既有修改细节时查 `CHANGELOG.md` 与 `docs/DEVELOPMENT.md`。这些文件承担项目状态与交接职责，不另建重复的任务或状态文件。

## 当前实现与保护

- `index.html` 是当前游戏的唯一开发入口。
- `versions/v0.1.0/index.html` 是本次登记的初始游戏快照。
- `versions/prototype/261026-pelican-ride.html` 是早期动画原型。
- 历史快照不覆盖；修改前识别并保留作者已有改动。
- 当前为 SVG 与原生 JavaScript 的离线单文件游戏。新增依赖、拆分文件或改变存档格式，应依据本次需求说明必要性，并同步入口和交接说明。
- 不把旧对话中的论文任务、研究规则或投稿要求带入本项目。

## 每次完成修改时

1. 给改动登记一个编号：`YYYYMMDD-NNN`。
2. 在 `docs/DEVELOPMENT.md` 写清需求、修改原因、修改前后行为、关键文件或函数，以及实际核对范围。
3. 为完成的改动增加版本号，保存新的 `versions/vX.Y.Z/index.html`。
4. 更新 `version.json` 的当前版本、快照与修改编号，并在 `CHANGELOG.md` 登记同一编号。
5. 若结构或后续工作变化，同步 `docs/HANDOFF.md`。新版本不得静默替换旧快照。

使用修改编号与版本快照追溯内容，不为一般开发添加哈希或重复完整性清单。

## GitHub 开发与发布

- 用户于 2026-10-27 授权建立公开仓库 `ScarfQian/pelican-knight` 并通过 GitHub Pages 首次发布。仓库为 `https://github.com/ScarfQian/pelican-knight`，在线地址为 `https://scarfqian.github.io/pelican-knight/`。
- 首次上传用于初始化 `main`。后续修改在独立功能或修复分支完成；本地文件、版本快照和日志仍在本目录维护。
- 按用户当前指令提交、推送分支和创建 PR。PR 应说明行为变化及实际验证范围，不得把未运行的检查写成通过。
- 是否合并到 `main` 由用户逐次决定。未经用户明确同意，不合并、不启用自动合并、不直接推送维护内容到 `main`，也不绕过分支保护。
- GitHub Pages 从 `main` 根目录发布，合并后更新在线游戏；分支或未合并 PR 不改变正式在线版。
- 保留旧版本与历史；不强推、不改写历史，不引入额外构建或测试依赖。

## 验证与说明

用户在初始创作中要求不使用 Skill、不依赖原有本地 AGENTS.md、不运行测试，本次迁移继续遵守。新的对话按用户当次授权开展工作；若开展浏览器试玩、移动端或自动化测试，必须记录实际环境、步骤与结果。不要将代码存在、文件可读或迁移成功写成玩法验证完成。

不擅自更改暂停、升级、胜负条件或存档的既定含义；需要改动时在日志交代行为变化。除用户明确要求外，不发布到外部服务，不修改无关目录。
