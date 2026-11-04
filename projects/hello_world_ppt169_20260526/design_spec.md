# Hello World - Design Spec

> Human-readable design narrative. Machine-readable execution contract: `spec_lock.md`.

## I. Project Information

| Item | Value |
| ---- | ----- |
| **Project Name** | hello_world |
| **Canvas Format** | PPT 16:9 (1280×720) |
| **Page Count** | 3 |
| **Design Style** | A) General Versatile + 简约现代 |
| **Target Audience** | 通用演示/测试用途 |
| **Use Case** | 功能测试 — 验证生图流程 |
| **Created Date** | 2026-05-26 |

---

## II. Canvas Specification

| Property | Value |
| -------- | ----- |
| **Format** | PPT 16:9 |
| **Dimensions** | 1280×720 |
| **viewBox** | `0 0 1280 720` |
| **Margins** | left/right 60px, top/bottom 50px |
| **Content Area** | 1160×620 |

---

## III. Visual Theme

### Theme Style

- **Style**: 简约现代
- **Theme**: Light theme
- **Tone**: 清爽、专业、简洁

### Color Scheme

| Role | HEX | Purpose |
| ---- | --- | ------- |
| **Background** | `#FFFFFF` | 页面背景 |
| **Secondary bg** | `#F3F4F6` | 卡片背景 |
| **Primary** | `#2563EB` | 标题装饰、关键区域、图标 |
| **Accent** | `#10B981` | 数据高亮、关键信息 |
| **Body text** | `#1F2937` | 正文文本 |
| **Secondary text** | `#6B7280` | 注释、说明文字 |
| **Border/divider** | `#E5E7EB` | 卡片边框、分隔线 |

### AI Image Strategy

- **Image Rendering**: vector-illustration
- **Image Palette**: cool-corporate

---

## IV. Typography System

### Font Plan

**Typography direction**: modern CJK sans (协调方案)

| Role | Chinese | English | Fallback tail |
| ---- | ------- | ------- | ------------- |
| **Title** | `"Microsoft YaHei", "PingFang SC"` | `Arial` | `sans-serif` |
| **Body** | `"Microsoft YaHei", "PingFang SC"` | `Arial` | `sans-serif` |

**Per-role font stacks**:

- Title: `"Microsoft YaHei", "PingFang SC", Arial, sans-serif`
- Body: `"Microsoft YaHei", "PingFang SC", Arial, sans-serif`
- Code: `Consolas, "Courier New", monospace`

### Font Size Hierarchy

**Baseline**: Body font size = 24px (relaxed)

| Purpose | Ratio to body | Value | Weight |
| ------- | ------------- | ----- | ------ |
| Cover title | 3x | 72px | Bold |
| Page title | 1.5x | 36px | Bold |
| Subtitle | 1.25x | 30px | Regular |
| **Body content** | **1x** | **24px** | Regular |
| Annotation | 0.75x | 18px | Regular |
| Page number | 0.58x | 14px | Regular |

---

## V. Layout Principles

### Page Structure

- **Header area**: 50px, page title
- **Content area**: 570px, main content
- **Footer area**: 50px, page number

### Spacing Specification

**Universal**:

| Element | Current Project |
| ------- | --------------- |
| Safe margin from canvas edge | 60px |
| Content block gap | 32px |
| Icon-text gap | 12px |

---

## VI. Icon Usage Specification

### Source

- **Built-in icon library**: `templates/icons/chunk-filled/`
- **Library**: chunk-filled

### Recommended Icon List

| Purpose | Icon Path | Page |
| ------- | --------- | ---- |
| 地球/世界 | `chunk-filled/globe` | P01, P02 |
| 代码 | `chunk-filled/code` | P02 |
| 火箭 | `chunk-filled/rocket` | P03 |

---

## VII. Visualization Reference List

Catalog read: 71 templates

本项目为简单 3 页 Hello World，无数据可视化需求。fewer than 3 viz pages — no visualization templates selected.

---

## VIII. Image Resource List

| Filename | Dimensions | Ratio | Purpose | Type | Layout pattern | Acquire Via | Status | Reference | text_policy | page_role |
| -------- | ---------- | ----- | ------- | ---- | -------------- | ----------- | ------ | --------- | ----------- | --------- |
| hello_world_hero.png | 1280x720 | 1.78 | P01 封面氛围背景 — 代表"Hello World"编程入门概念 | Illustration | #1 full-bleed background with floating title + #29 two-stop scrim | ai | Pending | A friendly computer terminal screen floating in space with colorful brackets and angle-bracket symbols radiating outward; calm center area for title overlay; sense of beginning and discovery | none | hero_page |

---

## IX. Content Outline

### Part 1: Hello World

#### Slide 01 - 封面

- **Layout**: Full-bleed background image + centered title (hero_page)
- **Title**: Hello, World!
- **Subtitle**: 一切伟大的旅程从这里开始
- **Info**: 2026

#### Slide 02 - 什么是 Hello World

- **Layout**: Left icon-text + right content body
- **Title**: 什么是 Hello World?
- **Content**:
  - 程序员学习新语言的第一个程序
  - 1972年由 Brian Kernighan 首次使用
  - 已成为编程文化的象征符号

#### Slide 03 - 结语

- **Layout**: Single column centered
- **Title**: 开始你的编程之旅
- **Content**:
  - 每一行代码都是一次探索
  - Hello World 是起点，不是终点
  - 🚀 Let's Go!

---

## X. Speaker Notes Requirements

- **Filename**: match SVG name
- **Total duration**: 2 minutes
- **Style**: conversational
- **Purpose**: inform

---

## XI. Technical Constraints Reminder

1. viewBox: `0 0 1280 720`
2. Background uses `<rect>` elements
3. Text wrapping uses `<tspan>` (`<foreignObject>` FORBIDDEN)
4. Transparency uses `fill-opacity` / `stroke-opacity`; `rgba()` FORBIDDEN
5. FORBIDDEN: `mask`, `<style>`, `class`, `foreignObject`, `textPath`, `animate*`, `script`
6. `<g opacity="...">` FORBIDDEN; set on each child individually
7. Inline styles only; external CSS FORBIDDEN
