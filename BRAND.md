# MIGO FIT — Brand Identity Guidelines

> **MIGO FIT** = Your AI Workout MIGO  
> 你的 AI 健身好朋友

本文档定义 MIGO FIT 的品牌视觉规范，**所有 App / 网站 / 营销物料 / 客服回复 / 媒体素材** 必须遵循。

---

## 1. 品牌定位

### 中英文品牌名

| 场景 | 表达 |
|------|------|
| 英文主名 | **MIGO FIT**（全大写，两词之间 1 个空格）|
| 英文简称 | **MIGO** |
| 中文译名 | **米高** *或* **米高 FIT** |
| App Store 显示名 | **MIGO FIT** |
| 应用商店副标题 | 你的 AI 健身好朋友 |

### 一句话定位

> **MIGO FIT 是一位 24 小时陪你练的智能教练，让科学训练像和朋友健身一样轻松自然。**

### 品牌词根解读

- **MIGO** ← 源自西班牙语 **amigo（朋友）** 的简化  
  - 5 亿西语母语用户秒懂
  - 英语世界通过流行文化普及（电影/音乐中 "Hey, amigo" 极高频）
  - 中文译名「米高」自带乔丹 (Michael Jordan) 联想，气势在线

- **FIT** ← Fitness 的核心词  
  - 全球通用，无文化壁垒
  - 双关：身体的"合身" + 训练的"健康"

### Slogan 体系

| 场景 | Slogan |
|------|--------|
| **主 slogan（中文）** | 你的 AI 健身好朋友 |
| **主 slogan（英文）** | Your AI Workout MIGO |
| **行动召唤（中文）** | 和 MIGO 一起动起来 |
| **行动召唤（英文）** | Move with MIGO |
| **App Store 副标题** | AI 姿态识别 + 实时纠正，像私教一样陪你练 |

---

## 2. Logo 体系

### 2.1 Logo Mark（主标识，方形）

**文件**：[`assets/logo.svg`](assets/logo.svg)

- 圆角矩形背景（22% 圆角率，符合 iOS/Android 规范）
- 渐变填充：品牌主渐变 `#FF4D4F → #FFA940`
- 白色字母 M：两座山峰，象征"目标的起伏与征服"
- **用途**：App Icon、社交媒体头像、印刷品方形位、Favicon

### 2.2 Logo Wordmark（完整水平标识）

**文件**：[`assets/logo-wordmark.svg`](assets/logo-wordmark.svg)

- 左侧 Logo Mark + 右侧 "MIGO FIT" 文字
- "MIGO" 深灰 + "FIT" 品牌渐变（强化色彩记忆）
- **用途**：网站 Header、邮件签名、文档头、PPT 封面、名片

### 2.3 Logo 使用禁区

❌ **绝不允许**：
- 拉伸变形 Logo
- 改变 Logo 颜色（非渐变版本除外，见 2.4）
- 在 Logo 周围 0.5 倍 Logo 高度内放置其他元素
- 把 Logo 放在低对比度背景上（如黄色/红色背景）
- 给 Logo 加阴影/描边/特效（除官方提供的微弱 drop-shadow）

### 2.4 单色版本（兼容低墨/低色彩场景）

未来如需印刷或单色场景，提供：
- **纯白版本**：在深色背景上使用
- **纯黑版本**：在浅色背景上使用
- **纯灰版本**：在文档正文中使用

（当前阶段暂未生成，按需创建）

---

## 3. 配色规范

### 3.1 品牌主色（强制使用）

| 用途 | 色值 | 示意 | 使用频率 |
|------|------|------|---------|
| **主色 Primary** | `#FF4D4F` | 🟥 温暖红 | 高（CTA 按钮、强调色）|
| **主色暗** | `#D9363E` | 🟥 深红 | hover / pressed 状态 |
| **辅色 Accent** | `#FFA940` | 🟧 活力橙 | 渐变结束、辅助强调 |
| **品牌主渐变** | `#FF4D4F → #FFA940` | 🟥🟧 | Hero / Logo / 关键 CTA |

### 3.2 中性色

| 用途 | 色值 |
|------|------|
| 主文字 | `#1F1F1F` |
| 次要文字 | `#595959` |
| 三级文字 | `#8C8C8C` |
| 背景 | `#FFFFFF` |
| 软背景 | `#FAFAFA` |
| 分区背景 | `#F5F5F7` |
| 边框 | `#EAEAEA` |

### 3.3 功能色

| 用途 | 色值 |
|------|------|
| 成功 / 通过 | `#4CAF50` |
| 警告 | `#FFB74D` |
| 错误 | `#FF5252` |
| 信息 | `#5B8DEF` |

### 3.4 肌群主题色（App 内）

| 肌群 | 色值 |
|------|------|
| 胸 Chest | `#FF6B6B` |
| 背 Back | `#5B8DEF` |
| 腿 Legs | `#2ED8A3` |
| 肩 Shoulders | `#FFB347` |
| 臂 Arms | `#A78BFA` |

> 详见 [`FitCoachRN/src/common/theme/colors.ts`](../FitCoachRN/src/common/theme/colors.ts)

---

## 4. 字体规范

### 4.1 中文字体

| 场景 | 字体（按优先级降级）|
|------|------------------|
| 默认 | PingFang SC（苹方）→ Microsoft YaHei（微软雅黑）→ 系统默认 |
| 标题 | 同上，加粗 `font-weight: 800` |

### 4.2 英文字体

| 场景 | 字体（按优先级降级）|
|------|------------------|
| 默认 | -apple-system → BlinkMacSystemFont → Segoe UI → Helvetica |
| 标题 | 同上，加粗 `font-weight: 800` |
| 等宽 / 代码 | SF Mono → Consolas → Monaco → monospace |

### 4.3 字号节奏

| 用途 | 大小 | 字重 |
|------|------|------|
| H1 (Hero) | 56px (移动端 36px) | 800 |
| H2 (Section) | 38px (移动端 28px) | 800 |
| H3 (Card) | 19-22px | 700 |
| Body | 16px | 400 |
| Caption | 14px | 400 |

---

## 5. 文案语调（Voice & Tone）

### 5.1 整体调性

- **像朋友说话**（"陪你练" / "和我一起" / "今天感觉怎么样"）
- **避免说教感**（不说"你必须" / "你应该"，改说"试试看" / "我们试试"）
- **温暖但专业**（数据驱动的鼓励，而非空洞口号）
- **中英文都要"轻盈感"**（短句优先、避免长定语）

### 5.2 常用文案模板

| 场景 | ✅ 推荐 | ❌ 避免 |
|------|--------|--------|
| 欢迎语 | "Hey，今天想练什么？" | "尊敬的用户，欢迎使用..." |
| 训练完成 | "今天的 MIGO 任务，完成 💪" | "训练任务已完成" |
| 动作纠正 | "膝盖再往外打开一点～" | "您的动作不标准，请调整膝盖位置" |
| 失败 | "稍微歇一下再来一次？" | "操作失败，请重试" |
| 付费引导 | "和 MIGO 一起解锁全部训练" | "立即开通会员获取完整功能" |

### 5.3 禁用词

- ❌ "用户"（→ 改成"你" / "MIGO 朋友"）
- ❌ "操作" / "点击"（→ 改成行动词，如"试试" / "看看"）
- ❌ "请您注意" / "您必须" / "您应当"（去除官方腔）

---

## 6. 应用场景规范

### 6.1 App 内

- 启动画面 = Logo Mark + 渐变背景 + Slogan
- 导航栏 = Logo Mark（左上 32px）+ 当前页面标题
- 主 CTA 按钮 = 品牌主渐变背景 + 白色文字
- 次 CTA 按钮 = 透明背景 + 主色边框 + 主色文字

### 6.2 网站

- Header = Logo Mark (32px) + "MIGO FIT" 文字
- Hero = 品牌主渐变背景 + 白色大标题
- Footer = 深色背景 (`#1F1F1F`) + Logo + 公司信息

### 6.3 微信生态

- 公众号头像 = Logo Mark（导出 400×400 PNG）
- 小程序图标 = 同上
- 朋友圈分享卡片标题：固定 "MIGO FIT — 你的 AI 健身好朋友"

### 6.4 App Store / Google Play

- **应用名**：MIGO FIT
- **副标题**：你的 AI 健身好朋友
- **关键词**（中文）：AI 健身, 私教, 姿态识别, 健身教练, 智能纠正, 在家健身
- **关键词**（英文）：AI Fitness, Personal Trainer, Pose Detection, Smart Workout, Home Fitness
- **截图统一风格**：主渐变背景 + 白色大字标题 + 设备框 mockup

---

## 7. 公司信息（页脚 / 版权用）

| 字段 | 值 |
|------|-----|
| **公司全称** | 北京跃动无限科技有限公司 |
| **English Name** | Beijing Yuedong Wuxian Technology Co., Ltd. |
| **联系邮箱** | 1348270542@qq.com（建议后续切换为 hello@migofitai.com 企业邮箱）|
| **应用官网** | [https://migofitai.com](https://migofitai.com)（备案完成后正式启用）|
| **API 域名** | `api.migofitai.com`（生产环境后端入口）|
| **版权年份** | © 2025-2026 |

---

## 8. 文件清单

| 文件 | 用途 |
|------|------|
| [`assets/logo.svg`](assets/logo.svg) | 主 Logo Mark（方形 100×100，可放大无损）|
| [`assets/logo-wordmark.svg`](assets/logo-wordmark.svg) | 完整水平 Logo（Mark + Wordmark）|
| [`assets/favicon.svg`](assets/favicon.svg) | 浏览器标签页图标（32×32）|
| [`assets/style.css`](assets/style.css) | 网站全站样式 + CSS 变量定义 |

**App Icon 导出指南**：使用 [`assets/logo.svg`](assets/logo.svg) 通过任意 SVG→PNG 工具（如 [CloudConvert](https://cloudconvert.com/svg-to-png) 或 ImageMagick）导出以下尺寸：

```
iOS:     1024×1024（必备）+ 60/76/120/152/167/180 等
Android: 48/72/96/144/192/512 （xxxhdpi 必备 192）
微信小程序: 144×144
公众号:  400×400 头像 + 200×200 缩略
```

---

## 9. 版本历史

| 版本 | 日期 | 变更 |
|------|------|------|
| v1.0 | 2026-05-28 | 初次品牌 VI 发布（从 FitCoach 改名为 MIGO FIT）|
