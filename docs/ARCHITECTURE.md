# 单文件架构与铁律 (Architecture & Rules)

打工人小账本的核心约束只有一条：**一个 HTML 文件，双击即用，零依赖，真·离线**。
下面把这条约束拆成可执行的铁律，供后续迭代遵守。

---

## 一、铁律

1. **单文件**：所有 HTML / CSS / JS / SVG 内联在同一个 `.html` 里，无构建步骤，双击即用。
2. **零外链**：不引用任何 CDN / 框架 / 外部字体 / 在线图表库。
   - 图表用**内联 SVG 手写**（折线、饼图、柱状、进度环）。
   - 图标用**内联 SVG path**，**严禁用 emoji 当图标**。
   - 字体用系统字体栈：`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "PingFang SC", "Microsoft YaHei", sans-serif`。
3. **数据本地**：localStorage（key 前缀 `wb_ledger_`），刷新 / 关闭不丢。
   - 必须支持 JSON 导入导出（不限条数）+ CSV 导出。
   - 清空全部需二次确认；满 30 条顶部提示备份。
4. **移动优先**：窄屏（<880px）单列、底部 Tab；按钮 ≥ 44px；输入框 ≥ 16px（防 iOS 缩放）；适配 `env(safe-area-inset-bottom)`。
   - 已加 `apple-mobile-web-app-capable` + `theme-color`，添加到主屏幕可全屏像 APP。
   - `touch-action: manipulation` 消除点击延迟；`text-size-adjust: 100%` 防系统乱缩放。
5. **预置示例数据**：首次打开有示例且标记 `isDemo`，可单独「安全清理示例数据」，绝不让首屏空白。
6. **国内习惯**：支出红 / 收入绿；货币 `¥`；日期 `YYYY-MM-DD`。

---

## 二、状态与模块边界

- 状态集中在 `S` 对象：`records / fixed / settings / freedom / seeded`，统一 `load(k,def)` / `save(k,v)`。
- 核心模块不超过 3–4 个；加功能走「加 1 个模块」迭代，不一次堆砌。
- 新模块数据用新 key，不影响老数据（向后兼容）。

---

## 三、如何加一个新模块

1. 在 `<aside class="nav">` 加一个 `nav-btn`（**内联 SVG 图标**，不用 emoji）。
2. 加一个 `<section id="xxx">` 并在 `switchTab()` 增加分支。
3. 数据进 `S` + localStorage，写对应渲染函数。
4. 新图表一律内联 SVG，不引外部库。

---

## 四、文件即源码

- 应用本体 = 源码，无需编译。改完直接在浏览器双击验证。
- 发布：Git Tag（如 `v1.0.0`）+ GitHub Releases；版本记录见 `CHANGELOG.md`。
- 中英文文档两份（`README.md` / `README_EN.md`）；应用内文案以中文为主，后续可加 i18n。

---

## 五、项目目录（存放规范）

```
dagongren-ledger/
├── 打工人小账本.html     # 唯一产物（单文件、零依赖、全内联、真·离线）
├── README.md            # 中文文档
├── README_EN.md         # English documentation
├── LICENSE              # MIT
├── docs/
│   ├── ROADMAP.md       # 迭代路线（吸收自同类 + 我们的创新）
│   ├── ARCHITECTURE.md  # 本文件
│   └── CHANGELOG.md     # 版本记录
└── assets/              # 预览截图 / PWA 图标（当前全内联，留占位）
```
