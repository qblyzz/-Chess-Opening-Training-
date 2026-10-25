# 开局训练室 · 国际象棋开局训练软件

一个**离线可用**的国际象棋开局学习与训练程序：47 个经典开局、151 条主线与变例、2374 步棋，
每一步都配中文讲解；棋盘交互参考 lichess（拖动/点击走子、合法着法提示、升变选择、箭头标注、平移动画、多种配色）。

规则引擎为**自研零依赖实现**，并通过国际通用的 perft 基准测试全项验证（见下文「正确性验证」）。

---

## 一、怎么打开（三种方式）

| 方式 | 操作 | 说明 |
|---|---|---|
| **① 桌面快捷方式（推荐）** | 双击 `创建桌面快捷方式.bat`，然后双击桌面上的「开局训练室」 | 独立应用窗口，无地址栏、无命令行黑窗，图标是象棋王 |
| **② 直接启动** | 双击 `启动开局训练室.vbs` | 同上，只是不创建快捷方式 |
| **③ 浏览器标签页** | 双击 `启动软件.bat` | 在浏览器标签页里打开，适合调试或多窗口对照 |

启动后是一个**独立应用窗口**（Edge/Chrome 的应用模式），关闭窗口即自动停止后台服务，不会残留进程。

> 前置条件：本机需要安装 [Node.js](https://nodejs.org/)（用于启动本地服务，不联网、不下载任何东西）。
> 如果只想要「装好即用」的桌面应用，见下一节的 PWA 安装。

### 安装为系统应用（PWA，可离线）

在应用窗口/浏览器里打开后，右上角会出现 **「⬇ 安装」** 按钮（若没有，点地址栏右侧的安装图标）。
安装后：

* 出现在 Windows 开始菜单与桌面，可固定到任务栏；
* 独立窗口运行，`start_url` 直达开局库，并带「开始训练 / 今日复习 / 开局库」三个启动快捷方式；
* **完全离线可用** —— 首次打开后所有页面、脚本与开局数据都会缓存到本机，
  即使本地服务没有启动也能正常打开使用（已实测：关闭服务器后仍可完整加载）。

---

## 二、四种使用模式

### 📚 开局库（学习）

左侧按五大类浏览开局 → 展开某个开局 → 点任意变例，棋谱立即摆到棋盘上：

* 右侧「讲解」面板逐步显示中文说明，点击任意一步可跳转；
* `◀ ▶` 单步前后，`Space` 自动播放，`⏮ ⏭` 跳到开头/结尾；
* 可以在棋盘上**自由试走**：走出开局书以外的着法时会提示「已脱离线路」，并列出开局书推荐着法；
* 棋盘徽标实时显示当前局面属于哪个开局（与 lichess 的开局提示同理）；
* 「思路」面板给出双方战略要点，「走法」面板可复制走法/PGN，「局面」面板显示 FEN、子力与合法着法数。

### 🎯 训练（走法记忆）

选择范围（全部 / 按分类 / 当前开局 / 当前线路 / 到期复习 / 错题本）、执棋方（白 / 黑 / 都练）与难度层级后开始：

* 程序扮演对手自动走棋，轮到你时必须走出开局书上的正确着法；
* 走对 → 绿色提示 + 音效 + 该步中文讲解；走错 → 红色标记 + 立刻告诉你正确着法及其含义，可以重试；
* 「提示」按钮两级提示（先标出起点格，再画出完整箭头），「显示答案」会替你走并讲解；
* 侧栏实时显示进度、完美通过数、步数正确率与最长连对。

### 🧠 认开局（测验）

给出一个局面与四个选项（干扰项优先取同一首步、不同开局的线路，避免太容易），
答完立即显示该线路的完整走法与逐步讲解，并可一键跳到开局库学习。

### 🔁 复习（间隔重复）

每条线路放进一个「记忆盒」：答对升级（间隔 **1 → 3 → 7 → 16 → 35 → 70 天**），答错降两级并很快重新出现。
「今日到期」列表决定当天该复习哪些线路，错题本按错误次数排序。

### 📈 统计

训练次数、练过的线路、步数正确率、已掌握线路数、连续学习天数、最近 14 天训练量柱状图、
各开局掌握程度（已掌握线路 / 总线路），以及最近训练记录。

所有进度保存在本机浏览器的 `localStorage`，不上传任何数据；可在「设置」里导出/导入 JSON 备份。

---

## 三、快捷键

| 按键 | 作用 |
|---|---|
| `←` / `→` | 上一步 / 下一步 |
| `↑` / `↓` | 回到起始局面 / 跳到线路末尾 |
| `F` | 翻转棋盘 |
| `Space` | 自动播放 / 停止 |
| `H` | 提示 |
| `Esc` | 关闭弹窗 |
| 棋盘拖动 / 点击 | 走子（点击两次也可以） |
| 棋盘**右键拖动** | 画箭头；**右键单击**清除箭头 |

---

## 四、收录的开局

### 开放性开局（1.e4 e5）　（10 个开局 / 41 条线路）

| ECO | 开局 | English | 线路数 | 首个变例 |
|---|---|---|---|---|
| C23 | 飞象开局 | Bishop's Opening | 4 | 2...Nf6 主线 3.d3 c6 |
| C30 | 王翼弃兵 | King's Gambit | 4 | 接受弃兵主线 3.Nf3 g5 |
| C25 | 维也纳开局 | Vienna Game | 4 | 3.Bc4 主线（2...Nf6） |
| C42 | 俄罗斯防御 | Petrov Defence | 4 | 古典主线 3.Nxe5 d6 |
| C41 | 菲利多尔防御 | Philidor Defence | 3 | 主线 3.d4 exd4 |
| C45 | 苏格兰开局 | Scotch Game | 4 | 古典主线 4...Bc5 |
| C60 | 西班牙开局 | Ruy Lopez | 5 | 莫菲防御主线 3...a6 |
| C50 | 意大利开局 | Italian Game | 5 | 平稳变例（Giuoco Pianissimo） |
| C55 | 双马防御 | Two Knights Defense | 5 | 主线 4.Ng5 d5 5.exd5 Na5 |
| C47 | 四马开局 | Four Knights Game | 3 | 西班牙式 4.Bb5 |

### 半开放性开局（1.e4，黑方不走 e5）　（14 个开局 / 37 条线路）

| ECO | 开局 | English | 线路数 |
|---|---|---|---|
| B90 | 西西里防御 · 纳伊道夫变例 | Sicilian: Najdorf | 4 |
| B76 | 西西里防御 · 龙式（南斯拉夫攻击） | Sicilian: Dragon, Yugoslav Attack | 2 |
| B34 | 西西里防御 · 加速龙式 | Sicilian: Accelerated Dragon | 2 |
| B33 | 西西里防御 · 斯维什尼科夫 | Sicilian: Sveshnikov | 2 |
| B48 | 西西里防御 · 泰马诺夫 | Sicilian: Taimanov | 2 |
| B23 | 西西里防御 · 封闭式 | Sicilian: Closed | 2 |
| B51 | 西西里防御 · 莫斯科变例 | Sicilian: Moscow Variation | 2 |
| C11 | 法兰西防御 | French Defence | 5 |
| B12 | 卡罗-康防御 | Caro-Kann Defence | 3 |
| B01 | 斯堪的纳维亚防御 | Scandinavian Defence | 3 |
| B04 | 阿廖欣防御 | Alekhine Defence | 3 |
| B08 | 皮尔茨防御 | Pirc Defence | 3 |
| B06 | 现代防御 | Modern Defence | 2 |
| B00 | 尼姆佐维奇防御（1...Nc6） | Nimzowitsch Defence | 2 |

### 封闭性开局（1.d4 d5）　（9 个开局 / 28 条线路）

| ECO | 开局 | English | 线路数 |
|---|---|---|---|
| D37 | 后翼弃兵（拒吃） | Queen's Gambit Declined | 5 |
| D20 | 后翼弃兵（接受） | Queen's Gambit Accepted | 3 |
| D17 | 斯拉夫防御 | Slav Defence | 4 |
| E06 | 卡塔兰开局 | Catalan Opening | 3 |
| D02 | 伦敦体系 | London System | 3 |
| D08 | 阿尔宾反弃兵 | Albin Counter-Gambit | 3 |
| D07 | 奇戈林防御 | Chigorin Defence | 2 |
| D01 | 韦列索夫开局 | Richter-Veresov Attack | 2 |
| D05 | 科勒体系 | Colle System | 3 |

### 印度防御体系（1.d4 Nf6）　（7 个开局 / 25 条线路）

| ECO | 开局 | English | 线路数 |
|---|---|---|---|
| E48 | 尼姆佐-印度防御 | Nimzo-Indian Defence | 4 |
| E15 | 后翼印度防御 | Queen's Indian Defence | 3 |
| E97 | 王翼印度防御 | King's Indian Defence | 4 |
| D86 | 格伦菲尔德防御 | Grünfeld Defence | 3 |
| A70 | 贝诺尼防御 | Benoni Defence | 4 |
| A87 | 荷兰防御 | Dutch Defence | 4 |
| A52 | 布达佩斯弃兵 | Budapest Gambit | 3 |

### 侧翼开局（1.c4 / 1.Nf3 等）　（7 个开局 / 20 条线路）

| ECO | 开局 | English | 线路数 |
|---|---|---|---|
| A20 | 英国式开局 | English Opening | 4 |
| A09 | 列蒂开局 | Réti Opening | 3 |
| A01 | 尼姆佐维奇-拉森攻击 | Nimzo-Larsen Attack | 3 |
| A02 | 伯德开局 | Bird's Opening | 3 |
| A00 | 索科尔斯基开局（1.b4） | Sokolsky Opening | 2 |
| A00 | 匈牙利式开局（1.g3） | Hungarian Opening | 2 |
| A00 | 范克鲁伊斯开局（1.Nc3） | Van Geet Opening | 3 |

**合计：47 个开局 / 151 条线路 / 2374 步**

---

## 五、正确性验证

### 1. 走法引擎：perft 基准测试

```bash
node tools/perft.mjs --depth 4
```

对 6 个国际标准基准局面逐层统计叶子节点数，全部与公开参考值一致：

```
✅ 起始局面        perft(1..4) = 20 / 400 / 8902 / 197281
✅ Kiwipete        perft(1..4) = 48 / 2039 / 97862 / 4085603
✅ 局面 3（残局）   perft(1..4) = 14 / 191 / 2812 / 43238
✅ 局面 4（升变）   perft(1..4) = 6 / 264 / 9467 / 422333
✅ 局面 5          perft(1..4) = 44 / 1486 / 62379 / 2103487
✅ 局面 6          perft(1..4) = 46 / 2079 / 89890 / 3894594
```

这一步覆盖了王车易位、吃过路兵、升变、牵制、将军与将杀判定等全部边界情况。

### 2. 开局数据校验

```bash
node tools/check-openings.mjs --all
```

逐步回放每一条线路的每一步（含 SAN 记谱的 `+`/`#`、易位、升变），检查：

* 每一步是否合法（不合法会打印出错步数与当时的 FEN）；
* `startMoves` 是否为每条线路的前缀；
* 每条线路的 `comments` 是否与 `moves` 一一对应；
* 线路终点局面是否重复、id 是否唯一、ECO 代码是否合法。

### 3. 界面与流程自检

```bash
node tools/server.mjs            # 另开一个窗口保持运行
node tools/smoke.mjs --url="/index.html?selftest=1"
```

用无头浏览器真实加载页面，运行内置自检（引擎 perft、数据合法性、棋盘渲染、
走子/复位/面板切换/训练会话启动/复习与统计视图等 36 项），并回传结果。
也可以直接在页面里点右上角 **❔ → 运行自检** 查看同样的报告。

---

## 六、目录结构

```
index.html                 应用入口（PWA 清单、错误收集器、弹窗结构）
manifest.webmanifest       PWA 清单（可安装为桌面应用）
sw.js                      Service Worker（离线缓存）
启动开局训练室.vbs          隐藏命令行启动器（推荐）
创建桌面快捷方式.bat         生成桌面 + 开始菜单快捷方式
启动软件.bat                浏览器标签页方式启动

src/
  css/style.css            全部样式（主题、棋盘配色、响应式）
  js/
    chess.js               自研规则引擎（0x88 走法生成 / SAN / FEN / 和棋判定）
    pieces.js              棋子 SVG 图形（内联，无外部资源）
    board.js               棋盘组件（拖拽、提示点、升变、箭头、动画）
    sound.js               WebAudio 合成音效（无音频文件）
    store.js               进度存储（记忆盒 / 日志 / 设置 / 导入导出）
    openings.js            开局运行时索引（局面 → 开局 / 开局书着法）
    trainer.js             训练 / 复习 / 统计
    selftest.js            内置自检
    app.js                 主控制器
  data/
    openings.js            ⚠️ 自动生成，请勿手改
    raw/*.json             开局原始数据（按分类，人工/脚本维护）

assets/
  icon.svg                 应用图标源文件（含 maskable 版本）
  icons/*.png, icon.ico    生成好的各尺寸图标

docs/开局数据规范.md         数据格式说明（新增开局看这个）
tools/                     服务器、启动器、构建、校验、测试等脚本
```

---

## 七、开发与维护命令

```bash
node tools/build-data.mjs          # 由 src/data/raw/*.json 生成 src/data/openings.js
node tools/check-openings.mjs --all  # 校验全部开局数据
node tools/list-openings.mjs       # 打印开局清单（本文档的表格就是这么来的）
node tools/perft.mjs --depth 4     # 引擎 perft 测试
node tools/selfcheck.mjs           # 一键全量自检（perft + 数据 + 浏览器冒烟）
node tools/make-icons.mjs          # 重新生成应用图标（含 .ico）
node tools/create-shortcut.mjs     # 创建桌面 / 开始菜单快捷方式
node tools/launch-app.mjs          # 启动器（--tab 用标签页，--server-only 只开服务）
node tools/server.mjs --port 8788 --open
node tools/smoke.mjs --url="/index.html?selftest=1"   # 浏览器自检
node tools/shot.mjs                # 多分辨率截图（检查响应式布局）
```

### 新增一个开局

1. 编辑 `src/data/raw/<分类>.json`（格式见 `docs/开局数据规范.md`）；
2. `node tools/check-openings.mjs src/data/raw/<分类>.json` 校验到 0 错误；
3. `node tools/build-data.mjs` 重新生成 `src/data/openings.js`；
4. `node tools/smoke.mjs --url="/index.html?selftest=1"` 确认界面无回归。

数据里每条线路的每一步都带一条中文讲解，这是本软件的核心内容，
因此规范里明确要求「只写确实熟悉的经典变例，准确性优先于数量」。

---

## 八、常见问题

**Q：双击启动器没反应？**
看 `%LOCALAPPDATA%\ChessOpeningTrainer\launcher.log`，里面记录了每一步。
最常见原因是没装 Node.js（VBS 会弹窗提示）或没有 Edge/Chrome。

**Q：窗口打开了但一片空白 / 提示初始化失败？**
按 `F5` 刷新一次；页面底部会显示具体错误信息。
如果之前手动改过前端文件，可把 `sw.js` 里的 `CACHE` 版本号 +1 以清掉旧缓存。

**Q：8788 端口被占用？**
启动器会自动向后寻找可用端口（8789、8790…），日志里会写明实际端口。
也可以手动指定：`node tools/launch-app.mjs --port=9000`。

**Q：进度会丢吗？**
进度存在浏览器 `localStorage` 里，按「站点/应用」隔离。清理浏览器数据会清空进度，
建议定期在「设置 → 导出进度」保存一份 JSON。

**Q：为什么棋盘上走出开局书以外的着法会有提示？**
那是自由探索模式。当前局面若仍在开局库中，状态栏会列出开局书推荐着法；点击即可跳回正轨。

**Q：想只看某个分类 / 只练白方？**
训练页左侧选择范围（可按分类或当前开局）、执棋方与难度层级，右侧会实时预览卡片数量。

---

## 九、已知边界

* 内置的是**开局数据**而不是分析引擎，不提供 Stockfish 式的局面评估；
  「局面」面板给出的是子力对比与合法着法数。
* 认开局测验的干扰项来自本软件收录的开局，因此选项之间难度不完全一致。
* 开局线路为常见主变，深度多在 6–12 回合；进阶研究建议配合完整棋谱数据库。
