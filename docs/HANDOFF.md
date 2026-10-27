# 鹈鹕骑士 · 新项目与新对话交接

日期：2026-10-27  
项目所有者：ScarfQian  
记录：Codex

## 直接接手

唯一工作目录：

`/Users/qianweijin/Library/Mobile Documents/com~apple~CloudDocs/10-开发/2-Game/1-鹈鹕骑士`

当前版本为 **0.1.1**，由 [version.json](../version.json) 登记。唯一开发入口是 [index.html](../index.html)；[v0.1.1 快照](../versions/v0.1.1/index.html)保存首次在线发布的游戏内容，[v0.1.0 快照](../versions/v0.1.0/index.html)保留迁移后的初始内容。两个版本的游戏 HTML 内容相同。

前一开发对话：[鹈鹕骑行动画与肉鸽游戏](codex://threads/01a17b67-0395-71e0-8fcf-0c84ef558a23)。本目录已包含继续开发所需的源文件和说明，不需要恢复父对话中的论文工作。

## 当前交付状态

- 已完成游戏代码编写和全部开发文件迁移。
- 已登记初始版本、快照、变更记录与开发日志。
- 0.1.1 增加 GitHub 与 GitHub Pages 发布配置；首次远端发布结果见开发日志 `20261027-002`。
- 当前 HTML 是实现原型；尚未进行浏览器试玩、自动化测试、移动端实测或性能测试。
- 当前没有进行中的修改，也没有等待继续执行的既有功能任务。
- 用户此前要求不使用 Skill、不依赖其原有本地 AGENTS.md、不运行测试。此轮按要求仅完成代码编写与文件迁移核对；新需求由新对话中的用户指令界定。

## 运行与机制

直接用浏览器打开 `index.html`，无需安装依赖或构建。全部 CSS、SVG 图形、JavaScript 和合成音效逻辑内嵌在 HTML 中。

| 项目 | 代码中的定义 |
| --- | --- |
| 游戏状态 | `title`、`playing`、`upgrade`、`paused`、`won`、`lost` |
| 通关条件 | 生存时间达到 180 秒，且首领已被击败 |
| 首领登场 | 第 135 秒 |
| 敌潮事件 | 第 35、75、110、165 秒 |
| 玩家操作 | WASD／方向键，触屏虚拟摇杆 |
| 冲刺 | 空格或按钮；初始冷却 2.6 秒，持续约 0.19 秒，期间免伤 |
| 初始体力 | 100 |
| 初始鱼镖 | 伤害 14，间隔 0.68 秒，自动寻找附近目标 |
| 初始经验门槛 | 8，后续随等级提高 |
| 成长 | 12 类升级，随机三选一，各有叠加上限 |
| 敌人 | 螃蟹、海鸥、海胆、水母、精英螃蟹、寄居蟹首领 |
| 首领初始体力 | 1850，低于一半后强化弹幕及冲锋节奏 |
| 随机性 | 敌人入场、掉落、升级候选和部分场景装饰使用 `Math.random()` |
| 记录保存 | `localStorage` 键 `pelican-coast-best-v1` |

体力耗尽时失败。达到 180 秒但首领尚存时继续战斗，不按计时单独判胜。当前保存的只是最佳击退数、最长时间、胜利次数，没有局外永久属性成长。

## 代码位置速查

当前为单文件，应按标识符定位；后续编辑可能使行号变化。

| 位置或标识符 | 职责 |
| --- | --- |
| `<style>` | 页面、HUD、菜单、升级卡片与移动端布局 |
| SVG `<defs>` 中的 `art-*` | 角色、敌人、武器与环境图形 |
| `#camera` 及各图层 | 世界坐标、敌人、弹丸、掉落、效果与角色显示 |
| `GOAL`、`BOSS_AT` | 生存目标与首领登场时间 |
| `upgrades` | 升级名称、说明、等级上限及效果 |
| `kinds` | 敌人初始参数 |
| `makeGame`、`startGame` | 一局的数据初始化与重开 |
| `pauseGame`、`finish` | 暂停、胜负结算与本地纪录 |
| `spawnPoint`、`spawnEnemy`、`spawnDirector` | 入场位置、敌人创建与时间推进 |
| `updateEnemies` | 追击、远程攻击、首领预警和冲锋 |
| `updatePlayer`、`dash`、`renderPlayer` | 移动、冲刺、相机与骑行动画 |
| `fireFish`、`updateShots` | 自动攻击、弹丸移动和命中 |
| `updateSkills`、`rebuildOrbits` | 环绕海星与车铃冲击波 |
| `updateDrops`、`offerUpgrades`、`chooseUpgrade` | 经验拾取、升级暂停和选择 |
| `updateEffects`、`updateHUD` | 粒子、伤害数字及界面 |
| `keydown`、`keyup`、摇杆指针监听 | 桌面与触屏输入 |
| `frame` | requestAnimationFrame 游戏主循环 |

## 版本维护

当前采用 `versions/` 完整快照配合日志。每批完成修改后：

1. 更新版本号并增加独立快照，保留旧版本。
2. 在 `CHANGELOG.md` 和 `docs/DEVELOPMENT.md` 使用同一修改编号。
3. 更新 `version.json`，使其指向当前入口和该版本快照。
4. 根据本次实际工作记录验证结果；不要把尚未进行的试玩写成通过。

用户已授权初始化 Git 并首次发布到公开仓库 [ScarfQian/pelican-knight](https://github.com/ScarfQian/pelican-knight)。在线地址为 [鹈鹕骑士](https://scarfqian.github.io/pelican-knight/)，GitHub Pages 发布来源为 `main` 根目录。旧可视化目录中的两份 HTML 已迁出，不回到旧路径修改。

后续按用户需求在本目录的新分支修改，完成版本、快照与日志后，按其指令提交、推送并创建 PR；由用户明确决定是否合并。未经同意不直接推送维护改动到 `main`，不自动合并。合并到 `main` 后在线版随 Pages 部署更新；未合并分支不会改变在线版。保留历史，不强推或改写提交。

## 存档说明

玩家纪录保存在浏览器，不在 HTML 源文件中。本次没有访问浏览器存储；移动路径后的存档可见性取决于浏览器的本地文件存储规则，不将开发文件迁移描述成玩家存档迁移。后续若需要导入、导出或统一存档，应作为单独功能处理。

## 可复制到新对话的提示

> 这是《鹈鹕骑士》海岸生存肉鸽游戏。请仅以 `/Users/qianweijin/Library/Mobile Documents/com~apple~CloudDocs/10-开发/2-Game/1-鹈鹕骑士` 为工作目录。先读取 README.md、version.json 和 docs/HANDOFF.md，再结合 index.html 处理我接下来提出的具体需求。当前登记版本是 0.1.1，公开仓库为 ScarfQian/pelican-knight；独立分支维护，按用户指令上传并创建 PR，由用户决定是否合并到 main 并更新在线版。保留旧快照，每次修改更新版本与日志。本次先恢复上下文，不自动开展试玩、测试、新功能或远端写入。
