# 基金对比分析报告 - 项目维护文档

> 本文档供其他 Agent 接管维护使用，包含完整项目上下文和技术细节。

---

## 项目概述

**名称**：三只基金对比分析报告
**仓库**：https://github.com/villiama818/fund_analyze
**在线地址**：https://villiama818.github.io/fund_analyze
**数据区间**：2020年1月 - 2026年5月
**对比基金**：

- 华泰柏瑞红利低波 ETF (512890.SH) - 被动指数
- 博道远航 A (007126.OF) - 杨梦 量化投资
- 大成睿享 A (008269.OF) - 徐彦 主动管理

---

## 技术栈

- **前端**：HTML5 + CSS3 + Vanilla JavaScript
- **图表**：Chart.js 4.4.0 (CDN)
- **字体**：Plus Jakarta Sans + Outfit (Google Fonts)
- **部署**：GitHub Pages (静态托管)

---

## 设计系统

### 色彩方案 (Dark Theme)

```css
:root {
    --bg: #000000;           /* 纯黑背景 */
    --surface: #0a0a0a;      /* 卡片/模块背景 */
    --surface-hover: #111111;
    --border: #1a1a1a;       /* 边框 */
    --text: #ffffff;         /* 主文字 */
    --text-muted: #666666;   /* 辅助文字 */
    --gold: #d4a847;        /* 强调色/标题 */
    --green: #2dd4a8;       /* 大成睿享/正收益 */
    --green-dim: rgba(45, 212, 168, 0.12);
    --red: #f87171;          /* 红利低波/负收益 */
    --red-dim: rgba(248, 113, 113, 0.12);
    --blue: #60a5fa;         /* 博道远航 */
    --blue-dim: rgba(96, 165, 250, 0.12);
    --gold-dim: rgba(212, 168, 71, 0.12);
}
```

### 字体

- **标题**：Plus Jakarta Sans (Google Fonts)
- **正文**：Outfit (Google Fonts)

### 圆角

```css
--radius-lg: 12px;  /* 大卡片 */
--radius-md: 8px;   /* 中等元素 */
--radius-sm: 4px;  /* 小按钮/标签 */
```

### 间距系统

- Container padding: 40px 32px (PC) / 24px 16px (Mobile)
- 模块间距: 40px (PC) / 24px (Mobile)
- 卡片内边距: 24px

---

## 文件结构

```
/Users/qsy/Desktop/基金研究/
├── index.html          # 主页面 (交付物)
├── hero-bg.png         # 头部背景图
├── fund-report.pdf     # PDF 报告下载链接
├── README.md          # 项目说明
└── .git/              # Git 仓库
```

---

## 页面结构

1. **Header Hero** - 大图背景 + 标题渐变融合
2. **Fund Cards** - 三只基金概览卡片（收益/波动率 + 基金经理背景详情）
3. **年度收益率对比** - 表格（年份/市场特征/各基金收益/冠军标记）
4. **累计净值走势对比** - 折线图 + 走势分析卡片
5. **风险收益指标** - 柱状图 + 雷达图 + 图例
6. **投资风格定位 & 核心指标排名** - 散点图 + 指标排名表格（并排）
7. **基金特征对比** - 特征卡片（策略/持股/换手率/估值等）
8. **Footer** - 风险提示 + PDF 下载链接

---

## 核心功能

### 图表类型

| 图表     | 类型    | ID            | 说明               |
| ------ | ----- | ------------- | ---------------- |
| 年度收益率  | Bar   | -             | 2020-2026 各年收益对比 |
| 累计净值走势 | Line  | netValueChart | 折线图，平滑曲线，填充效果    |
| 风险收益指标 | Bar   | riskChart     | 竖向柱状图            |
| 雷达图    | Radar | radarChart    | 多维度对比            |

### 交互功能

- **主题切换**：右上角按钮可切换 Light/Dark 模式
- **Tweaks 面板**：右下角悬浮按钮，可调节主题、圆角、间距
- **响应式**：三档适配 (1100px / 768px / 480px)

### 背景图处理

- PC：铺满 550px 高度，`cover` 裁切
- Mobile：`auto 100%` 按高度等比缩放
- 渐变融合：四边黑边渐变

---

## 基金经理信息

| 基金       | 经理   | 职位          | 投资理念                           |
| -------- | ---- | ----------- | ------------------------------ |
| 红利低波 ETF | 被动管理 | -           | 跟踪指数，透明稳定，规则驱动                 |
| 博道远航 A   | 杨梦   | 博道基金量化投资总监  | 双均衡多因子框架，基本面+量价，AI模型，管理规模超100亿 |
| 大成睿享 A   | 徐彦   | 大成基金首席权益投资官 | 从业17年，深度价值，低换手，不参与泡沫           |

---

## 响应式断点

| 断点      | 布局变化                            |
| ------- | ------------------------------- |
| ≤1100px | Grid → 单列                       |
| ≤768px  | 头部高度 280px，标题 1.5rem，图表 280px 高 |
| ≤480px  | 进一步微调字号                         |

---

## 维护指南

### 更新内容

1. **修改基金数据**：直接编辑 `index.html` 中的数值
2. **更换背景图**：替换 `hero-bg.png`，更新 `background: url()` 路径
3. **添加图表**：参考 Chart.js 官方文档，在 `scripts` 区块添加
4. **调整配色**：修改 `:root` 中的 CSS 变量

### 部署

```bash
cd /Users/qsy/Desktop/基金研究
git add .
git commit -m "your message"
git push
```

GitHub Pages 自动部署，等待 2-5 分钟生效。

---

## 相关资源

- [Web Design Engineer Skill](./web-design-engineer/SKILL.md)
- [Chart.js 文档](https://www.chartjs.org/docs/4.4.0/)
- [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans)
- [Outfit](https://fonts.google.com/specimen/Outfit)

---

## 更新日志

| 日期         | 版本   | 变更                        |
| ---------- | ---- | ------------------------- |
| 2026-05-27 | v1.0 | 初始版本 - 图表可视化报告            |
| 2026-05-27 | v2.0 | SpaceX 风格重设计，深色主题         |
| 2026-05-27 | v2.1 | 优化移动端适配，添加基金经理信息，PDF下载    |
| 2026-05-27 | v2.2 | 补全基金经理背景详情，增加投资风格定位散点图 |
| 2026-05-27 | v2.3 | 基金经理卡加职位名称，投资风格图与指标排名并排显示 |
| 2026-05-27 | v2.4 | 投资风格图与指标表格高度对齐，浅色模式换背景图 |
| 2026-05-27 | v2.5 | 新增系统主题自动适配（跟随系统深色/浅色模式） |