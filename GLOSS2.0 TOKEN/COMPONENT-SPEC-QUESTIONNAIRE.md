# GLOSS Vault 2.0 — 组件规范问卷

> 填写说明：在每个"你的答案"单元格里写下决定。不确定的写 "TBD"，完全按当前 Figma 的写 "按 Figma"，需要讨论的写 "讨论"。填完保存后发给 Claude 生成完整规范页面。

---

## A. 阴影系统（Elevation / Shadow）

已知：默认阴影是**双向 neumorphic**（上左浅白 + 下右暗黑），同一距离。

| # | 问题 | 我的理解/默认方案 | 你的答案 |
|---|------|------|----------|
| A1 | 默认"浮起"阴影的精确数值 | X=-3, Y=-3, Blur=6, Color=Overlay/LightHigher **+** X=3, Y=3, Blur=6, Color=Overlay/DarkLower |按 Figma |
| A2 | 是否有多个 elevation 层级？（比如 card / modal / tooltip / dropdown） | Card 用上面的；Modal/Dropdown 需要更深；Tooltip 更浅 — 需要你定每一级的数值 |业界常规 |
| A3 | Pressed（按下）状态：完全用 inset（内阴影）？还是减弱 drop 再加 inset？ | 完全 inset，相同距离和颜色 |减弱 drop 再加 inset |
| A4 | Hover（桌面端）：阴影变化吗？ | 阴影加深一级（X/Y 从 3→5，blur 不变） — 需要你确认 |阴影加深一级 |
| A5 | Focus 状态：用阴影（2px outline ring）还是用 border？ | 用 ring，颜色 Today/400（teal） |没看懂，ring和border什么区别？因为有过去现在未来三个主题所以不要用固定teal，所以用阴影加行业标准 |
| A6 | Disabled：是否去掉全部阴影？ | 去掉 drop，保留极浅 inset 表示"下沉" |去掉，字体也要变成disable的，如果要inset请确保和按下&输入的状态有明显区别，如果不能，请取消所有的阴影并差异化fill的颜色，使其看来确实disabled了 |
| A7 | Mobile 端是否用同样阴影？（有人认为移动端要更轻） | 同样，因为是品牌识别特征 | 同样，因为是品牌识别特征|
| A8 | 哪些组件**不**使用 neumorphic？（例如背景上的 divider、full-width banner） | Divider 不用；Banner 视情况 |Divider 不用；Banner 视情况 |

---

## B. 按钮层级（Button Hierarchy）

已知：有 Primary（teal "+" add 按钮）、顶部 TODAY/PAST/FUTURE 分段按钮。

| # | 问题 | 默认方案 | 你的答案 |
|---|------|------|----------|
| B1 | 按钮一共几级？ | Primary / Secondary / Tertiary / Ghost / Icon-only — 请确认并说明每一级用途 |这个需要业界常规规范一下，但是总共的按钮分为 行动确认按钮，取消按钮（比如popup左边取消右边确认，就是一个primary一个secondary），跳转按钮，保存按钮，toggle？tab？切换后选中状态按钮|
| B2 | Primary 填充色 | Surface/on-action（Today/550） |推测&业界常规 考虑主题色和accessiblity，有 轻微调整没关系 |
| B3 | Secondary 样式 | 白底 + Border/action 描边 1px + Text/action 文字 | 灰色底，不然阴影不明显，其他对的按照figma|
| B4 | Tertiary 样式 | 无底无边 + Text/action 文字；hover 时底色 Today/100 | 推测&业界常规|
| B5 | Destructive（删除/危险）按钮？ | 用 Error/500 红 — 是否需要独立定义 |有两种红，一个是in&out，用于transactions中花了钱的复数字体，另一个就是error的红 |
| B6 | 按钮尺寸分几档？（sm/md/lg） | sm:32px、md:40px、lg:48px（高度） | 可以，按照业界常规|
| B7 | 按钮圆角 | radius/md（6px） | 推测&业界常规|
| B8 | 按钮阴影策略 | Primary 有 neumorphic 阴影；Secondary/Tertiary 无 |secondary应该也有，但是tertiary无 |
| B9 | Pressed 阴影 | Primary 用 inner；Secondary 用 Today/100 底色反馈 | 可以按照推测&业界常规|
| B10 | Disabled 态 | Surface/disabled 底 + Text/disabled 文字，无阴影 | 对 按照figma|
| B11 | Loading 态设计 | 替换文字为 spinner，尺寸不变 |可以 推测&业界常规 |
| B12 | Mobile 最小触控区域 | 44x44pt（iOS HIG 标准） |好 请按照这个标准设计手机端按钮规范 |

---

## C. 条件配色规则（Conditional Color Logic）

已知：Balance 正→In/primary 绿，负→Out/primary 橙。

| # | 数据/状态 | 正向/成功色 | 负向/警示色 | 中性色 | 你的答案/补充 |
|---|------|------|------|------|----------|
| C1 | Balance 余额数字 | In/400（绿） | Out/400（橙） | — | 正=+，负=-，零走中性色，对 现在是body text secondary |
| C2 | Transaction 交易金额（收入 vs 支出） | In/400 | Out/400 | — | 收支都按这个标准来：正=+，负=-，零走中性色，对 现在是body text secondary（如果层级的命名不够规范可以帮我调整，但是要跟我说并确认了才行）|
| C3 | Trend 箭头（涨跌） | In/400 ↑ | Out/400 ↓ | Neutral/500（持平） |见上面 |
| C4 | Pending / Settled 状态徽章 | ? | ? | ? | 请定义 pending 用什么色 ：浅灰色，比持平要浅一级|
| C5 | Past / Today / Future 页面强调色 | Past=Orange, Today=Teal, Future=Indigo | — | — | 确认 |
| C6 | 通知四态 Info/Success/Warning/Error | Information / Success / Warning / Error 各自的 500 | | | 确认 |
| C7 | Chart 配色规则（饼图、折线图） | Today 系渐变用 Today/300-500？ | | | 确认 |
| C8 | 零值（例如 0.00 余额）是用哪个色？ | Neutral/500 灰 |确认 | | |

---

## D. 卡片 / Frame（Container）

| # | 问题 | 默认方案 | 你的答案 |
|---|------|------|----------|
| D1 | Card 默认圆角 | radius/lg（8px） |电脑端可以大一点，视觉上因为使用了新拟态，间隙不用在这么紧 |
| D2 | Card 默认内边距（Desktop / Mobile） | Desktop：24px；Mobile：16px |对  |
| D3 | Card 背景 | Surface/primary（Neutral/50） |不对，现在是Surface/Tertiary，请所有颜色都替换GLOSS Vault Design System 2.0中的颜色，不确定不标准的问我，我们一起讨论了改 |
| D4 | Card 默认阴影 | A1 中定义的双向 neumorphic |对 |
| D5 | Card Hover（如果是交互卡片）| 阴影加深一级 |可以 推测&业界常规 |
| D6 | Card Pressed/Active | 切换为 inset 阴影 |对，但是如果卡片里面还有 交互模块我不知道怎么办了，按照业界常规，这种情况应该比较少 |
| D7 | Card Selected（被选中） | Border/action 2px 描边 + 底色 Today/100 | 不确定是否要使用today的颜色，对于主题色和today是一个颜色这个问题我不太确定要怎么解决，请作为资深产品和ui设计帮我想解决方法|
| D8 | Card Disabled | 阴影移除 + 透明度 50% |确定 |
| D9 | 嵌套 Card（Card in Card）是否用阴影？ | 内层不用，用 Border/tertiary | 如果内层还嵌套有较大的模块可以再次使用阴影，其他情况按业界常规|

---

## E. 输入框 Input

| # | 问题 | 默认方案 | 你的答案 |
|---|------|------|----------|
| E1 | Input 高度（Desktop / Mobile） | Desktop 40px / Mobile 44px |desktop 为什么比mobile还小？desktop一般是46-58之间8的倍数 |
| E2 | Input 圆角 | radius/md（6px） | 8px|
| E3 | Input 默认底色 | Surface/tertiary（Neutral/200）按 mapping | 按业界常规应用设计系统已经有的颜色token |
| E4 | Input Border | 无 border，靠底色区分 — 或者 1px Border/tertiary | 按业界常规|
| E5 | Focus 态 | 2px Border/action + outline ring |按业界常规，但是不要使其在新拟态设计中过于违和和低保真化  |
| E6 | Error 态 | 2px Border/error + Error/500 文字提示 |按业界常规，但是不要使其在新拟态设计中过于违和和低保真化 |
| E7 | Disabled 态 | Surface/disabled + Text/disabled | 确认|
| E8 | Placeholder 色 | Text/disabled |应该是tertiary disable可能会导致看不清 |
| E9 | Label 位置 | Top（独立一行）；字号 body-sm |按业界常规 |

---

## F. 标签 / Chip / Badge

| # | 问题 | 默认方案 | 你的答案 |
|---|------|------|----------|
| F1 | Chip 使用场景 | 账户类型、tag 筛选、状态徽章 — 是否需要区分？ | 需要 categories表情是一种chips；view apge account filter中选中状态显示是一种类型；tag一般在account list查看的时候可能给不同账户，比如是手动添加的银行账户还是sync的，作以区分；以后的sync同步账户状态是一个类型；样式按照业界常规|
| F2 | Chip 圆角 | radius/round（pill 形） | 对|
| F3 | Chip 高度 | 24px（sm）/ 28px（md） | 可以 按照显示设备区分，但是要能看得清（accessiblity）|
| F4 | Status badge 的 Past/Today/Future 背景 | 用 Surface/{period}-secondary + Text/{period}-primary |看不懂 按业界常规 |
| F5 | 数字徽章（例如通知小红点）样式 | 圆形，Error/400 底 + 白字 |一般有提示黄色（非past橙色），报错error 完成 successful 绿色 |

---

## G. 导航（Navigation）
导航按照这个来写规范 https://www.figma.com/design/zrjDXFMGy03Z73xCDwFfvL/GLOSS-Vault-Design-System-2.0?node-id=474-10648&t=SJRMhtTADNDWAVDZ-1

| # | 问题 | 默认方案 | 你的答案 |
|---|------|------|----------|
| G1 | Desktop 左侧 Sidebar 宽度 | 240px | 对|
| G2 | Sidebar nav item 高度 | 36px |我记得是48px |
| G3 | Sidebar active 样式 | 背景 Surface/today-secondary + 文字 Text/action |做选中后颜色的差异化区别，注意手机端不能hover |
| G4 | Mobile 底部 Tab Bar 高度 | 56px（不含 safe area） |不是76吗？加home indicator总高度116（其实 我觉得有点高 能不能按照业界规范矮一点？） |
| G5 | Mobile Tab 选中样式 | 图标+文字都变 Text/action 色 |对 |
| G6 | 顶部分段控件（TODAY/PAST/FUTURE）| Pill 形，active 背景对应时态色 |对 |

---

## H. 响应式差异（Mobile vs Desktop）

| # | Token / 属性 | Desktop | Tablet | Mobile | 你的答案 |
|---|------|------|------|------|----------|
| H1 | Card padding | 24px | 20px | 16px | 按照行业规范|
| H2 | Card radius | 8px | 8px | 8px |按照行业规范 为了视觉上的透气性8-24均可 大卡片用24|
| H3 | 按钮最小尺寸 | 32px | 40px | 44px |如果都32了怎么去符合手机端最小44？按照行业规范调整 一般是36-58 |
| H4 | Body font size | 16px | 16px | 16px（不降） |可以降，不敢是因为怕accessiblity不符，保持不变如果ui丑的话可以改，按照行业规范调整，确保可读性就行 |
| H5 | H1 标题 | 60px | 48px | 32px | 当前 responsive 表三档都是 60，确认是否需要分档？需要，确保可读性 |
| H6 | 页面左右边距 | 32px | 24px | 16px | 一般24 像input form desktop 文本的左右边距24，手机端16|
| H7 | 阴影强度 | 标准 | 标准 | 减半？还是同样？ | 同样|

---

## I. 交互动效（Motion）

| # | 问题 | 默认方案 | 你的答案 |
|---|------|------|----------|
| I1 | 按钮 hover 过渡时长 | 150ms ease-out | 按照行业规范|
| I2 | 卡片 hover 过渡时长 | 200ms cubic-bezier(0.4,0,0.2,1) | 按照行业规范|
| I3 | Modal 打开动效 | 250ms fade + 轻微 scale up |你是说弹出scale up 之后又恢复原来大小的话不用，直接从小到标准大小或者滚动弹出都行，你帮我定一个用户视觉体验上更好的 |
| I4 | Page 切换（Past↔Today↔Future）| 需要颜色渐变过渡吗？300ms？ | 需要 智能动画渐变|
| I5 | Loading 动效 | Spinner 使用 Today/400 旋转 | |

---

## J. 原子结构分级（Atomic Design）
均按照行业标准，以及pfm personal financial management软件对应需求
| # | 层级 | 你想要包含哪些组件 | 你的答案 |
|---|------|------|----------|
| J1 | Atoms（原子）| Button, Icon, Input, Chip, Avatar, Spinner, Divider | |
| J2 | Molecules（分子）| Search Bar, Form Field (label+input+helper), List Item, Card Header | |
| J3 | Organisms（器官）| Account Card, Transaction List, Chart Card, Top Tab Bar, Sidebar | |
| J4 | Templates（模板）| Dashboard Layout, List Layout, Detail Page Layout | |
| J5 | Pages（页面）| Today Homepage, Accounts List, Account Detail | |

---

## K. 不一致/歧义（从 Figma 里我看到的问题）

这些是我在你的 Figma 里观察到的可能需要统一的点，请确认是有意为之还是需要修正：

| # | 观察到的不一致 | 你的答复 |
|---|------|----------|
| K1 | Mapping 层里 `Border/information` 映射到 `Warning/400`，`Border/warning` 映射到 `Information/400` — 看起来像反了 | 还真的反了，谢谢你 帮我调整|
| K2 | `Text/Infromation`（拼写）应该是 `Information` | 帮我改|
| K3 | `scale/150` 在 Light 是 6px，在 Dark 是 8px — 是有意的吗？ |不是是错的 按照行业规范帮我改 |
| K4 | `spacing/lg` Desktop/Tablet 是 24px，Mobile 突然降到 12px — 跨度很大，是否改为 16px 或单独定义 spacing/lg-mobile？ |可以加一个层级或者单独定义，帮我按照行业规范调整 |
| K5 | 目前只有 border-radius：none/sm/md/lg/lger/round，Chip 的 pill 形 和大圆角 card 使用同一个 round 吗？ |不是 帮我分开 是因为chip的标准还没写 |

---

**填完后：** 保存这个文档并告诉我，我会基于你的答案生成：
1. 新的"Components"sidebar section，按原子结构（Atoms / Molecules / Organisms）组织
2. 每个组件的 **All States**（default/hover/pressed/focus/disabled/loading/error）可视化
3. Desktop 和 Mobile 两套规范 tab
4. 每个组件配可复制的 token 引用和说明
5. 条件配色逻辑的 decision tree 可视化

我补充一点，所有design system 1的颜色需要根据 功能和使用规范在system2中规范，整理调整design system2的命名使表意清晰，并运用到我给你的两个figma链接页面中（accounts的和view&homepage的）（仅限该page）所有功能都能对应到正确合理的颜色，同时保持accessiblity
