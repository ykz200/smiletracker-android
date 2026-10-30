# 活 · Clock

> Pixel 3a 桌面摆件时钟 · Eternal Garden · 恒·园

基于 Pixel 3a 设备二次利用的桌面摆件时钟 PWA 应用。单文件交付，无框架无依赖。

## v15.0 "Eternal Garden / 恒·园" 新特性

- **Liquid Glass 11.0**：花瓣脉络纹理(`.glass-petal-vein`)、露珠凝结层(`.glass-dewdrop`)、湿度反射(`.glass-humidity`)、`--glass-petal-vein` / `--glass-dewdrop` / `--glass-humidity` 控制变量、虹彩旋转周期提升至 180s
- **Soul Clock 灵魂时钟**：第5种时钟面 — 12 时辰 × 12 种花卉（🌙🌑🌲🌅☕🌻🌸🌿🌺🌇🌃✨），每两小时切换花卉与氛围描述
- **情绪脉冲引擎**：`--bloom-level` / `--soul-humidity` / `--soul-warmth` 三变量联合控制全界面氛围
- **光合作用植被层** (`floralCanvas`)：飘动花瓣粒子系统，根据季节变化色调
- **苔藓光场层** (`mossCanvas`)：呼吸渐变光斑，营造禅意光场
- **花粉飘散层** (`pollenCanvas`)：超细粒子随风飘散，4 重叠加
- **OLED Care 4.0**：四重李萨如叠加 (±0.7px × 4)，更丝滑的像素漂移保护
- **深度色温 Circadian**：24+ 时区间连续插值，--pulse-warmth 动态控制
- **季节紫/绿滤镜**：春夏秋冬各自 hue-rotate + saturate 差异化处理
- **Bio-Rhythmic 2.0**：夜间降速因子引用更统一的 --breath-speed 变量
- **SDM670 帧率**：canvas DPR 限制最高 2.5，能效平衡
- **入场动画 5 级错峰**：app > * nth-child(1-5) 0.05s-0.33s 呼吸感入场
- **电池省电解模式增强 v15**：隐藏所有 canvas 背景，关闭文字阴影，降低模糊半径

## v14.0 "Luminous Veil" 特性（继承）

- **Liquid Glass 10.0**：脉络纹理、水波纹涟漪、52px 模糊、矿物质感
- **Sand Ripple 沙纹光场**：同心圆波动，低频养眼
- **Flow Light 流动光河**：缓慢流动光带粒子
- **季节色系 3.0**：饱和度调整范围约 ±0.2，不抢注意力
- **OLED Care 3.0**：三重李萨如、呼吸调制

## v13.0 "Zen Garden" 特性（继承）

- **沙纹涟漪**：枯山水 Canvas 背景层
- **矿物光泽**：液体玻璃质感
- **桌面场景预览**：Pixel 3a 设备机身渲染

## v12.0 "Aurora Weave" 特性（继承）

- **Aurora Weave 极光编织**：多层极光背景系统（nebula + aurora + neuralAurora 三层 Canvas 叠加）
- **Bio-Rhythmic 生物节律**：22:00-06:00 夜间所有动画自动放慢至 55% 速度
- **Weather Mood Canvas**：天气情绪色温层
- **桌面小水母「泡」**：天气与时段感知宠物
- **Circadian 节律背景**：24 小时色温插值系统

## 时钟模式

1. **数字钟面** — `numeric` — 超大数字 HH:MM:SS 显示
2. **指针钟面** — `analog` — SVG 绘制的模拟时钟，含时分秒针
3. **文字钟面** — `word` — 十二时辰 + 时段描述
4. **Flip 翻页钟面** — `flip` — 仿真翻页动画
5. **🆕 Soul 灵魂钟面** — `soul` — 十二时辰花卉变换，情绪氛围感

## 消息投递

```
?msg=内容&title=标题        # URL 投递
BroadcastChannel('pixel3a-clock')
localStorage.pixel3a-clock-inbox-v2
pushInboxMessage(title, body, opts)
```

## 资讯订阅

设置 → 资讯订阅 可增删 RSS / Atom 源、改刷新时间、填代理前缀。支持 CORS 代理自动回退链（3 个代理）。

## 纸条变量

| 变量 | 含义 |
|------|------|
| `{worked}` | 已工作时间（从 8:30 起） |
| `{countdown}` | 距下班倒计时 |
| `{weather}` | 天气图标 |
| `{temp}` | 温度 |
| `{toFriday}` | 距周五天数 |
| `{sunrise}` | 日出时间 |
| `{sunset}` | 日落时间 |
| `{solar_term}` | 临近的二十四节气 |
| `#quote` | 随机语录 |
| `#affirmation` | 随机自我肯定 |

## Canvas 背景系统

| 层级 | ID | 描述 |
|------|-----|------|
| 沙纹 | `sandRippleCanvas` | 同心圆波动 |
| 流动光 | `flowLightCanvas` | 光带粒子漂移 |
| 🆕 光合植被 | `floralCanvas` | 飘动花瓣粒子 |
| 🆕 苔藓光场 | `mossCanvas` | 呼吸渐变色斑 |
| 🆕 花粉飘散 | `pollenCanvas` | 超细飘散粒子 |
| 情绪 | `#bgMood` | 天气情绪色温 |
| 地平线光 | `horizonCanvas` | 昼夜光带 |
| 星云 | `nebulaCanvas` | 极光 1 |
| 极光 | `auroraCanvas` | 极光 2 |
| 神经极光 | `neuralAuroraCanvas` | 极光 3 |
| 日冕 | `coronaCanvas` | 日冕辉光 |
| 天气粒子 | `weatherParticles` | 雨雪粒子 |

## 技术栈

- 纯 HTML + CSS + JavaScript 单文件（零依赖）
- Service Worker 离线缓存
- PWA 可安装（fullscreen 模式）
- OKLCH 广色域感知色彩空间
- 语义化 HTML + ARIA 无障碍支持
- BroadcastChannel 跨标签页通信

## 文件结构

```
├── index.html              # 主文件（含所有 HTML/CSS/JS，v15 ~3800 行）
├── sw.js                   # Service Worker v15
├── manifest.webmanifest    # PWA 清单 v15
├── icon.svg                # 自适应 SVG 图标 v15
└── README.md               # 本文档
```

## Pixel 3a 适配

- 打孔屏安全区（竖屏 34px 顶部 padding；横屏摆件归零并改为左右 20px 侧安全区）
- OLED 纯黑背景 (#000) + 像素漂移保护（四重李萨如 ±1.2px 总振幅）
- SDM670 SoC 友好的自适应帧率（DPR 限制 ≤2.5）
- 环境光自适应亮度调节（42%-106%，平滑过渡）
- 电池 <15% 自动省电模式（关闭所有 canvas）
- 生物节律：夜间动画降速 55%，字重降至 340
- 地图使用 Open-Meteo（无需 API key）
- Weather + AQI 均走 Open-Meteo 双 API

## v15 深度检测

- [x] CSS 大括号平衡（约 `{` = 385, `}` = 385）
- [ ] JS 语法检查 (node --check — 浏览器 API 依赖可用环境验证)
- [x] DOM ID 引用一致性（约 90+ 个 getElementById 全部在 HTML 中有对应 id）
- [x] 标签闭合（HTML 5 head/body/html 完整闭合）
- [x] 新 Canvas 元素（floralCanvas/mossCanvas/pollenCanvas）已添加对应渲染系统
- [x] 灵魂钟面（faceSoul）HTML + JS 双端完整
- [x] OLED Care 4.0 四重李萨如数学正确
