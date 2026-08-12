# Dagongren Ledger (打工人小账本)

> A **single-file, zero-dependency, truly offline** personal finance workbench. It doesn't just record "how much you spent" — it converts every expense into "how many hours you worked", so both your money and your time become visible.

## The Problem It Solves

Most expense trackers only answer "where did my money go". But a wage earner's real anxiety is that **time is priced**: commuting, overtime, and a low hourly rate quietly eat your life.

Dagongren Ledger ties "bookkeeping" and "hourly wage" into one thread:

- Compute your **real hourly wage** (what each hour is actually worth after work costs, commute, and overtime)
- Every time you log an expense, instantly know "this cost you **X hours Y minutes of work**"
- Use **scenario simulation** to show: cutting commute by 30 min/day, reducing overtime, or a 10% raise — how much hourly wage and free time each buys back

## Core Features

- **Real hourly-wage calculator**: take-home monthly salary, pay months, work cost, on-site hours, commute, overtime — expands the formula step by step to a real hourly wage
- **10-second logging**: amount / category / note; on save it instantly converts "this ≈ X hours Y minutes of work"
- **Life ledger (core thesis)**: the home page converts this month's spending into the working days of your life you sold for it — see how many days you worked just to consume, not for yourself
- **Home overview**: this month's income / fixed expense / flexible expense / net balance, latest 4 records, native-SVG savings curve
- **Freedom fund & safety cushion**: progress bars visualize your financial buffer
- **Scenario simulation**: commute optimization / less overtime / raise, and their impact on hourly wage and free time
- **Editable records**: every entry can be edited (amount / category / note / date); expenses auto-recompute work-hours
- **Category budgets + alerts**: set a monthly cap per category; overspend or 80%-reach triggers red/yellow alerts on the home page
- **Expense pie chart**: a native-SVG donut on the home page shows where the money went
- **4-way filtering**: filter records by month + type + category + keyword
- **Data safety**: localStorage on-device, JSON import/export + CSV export + safe demo-data cleanup

## How It Differs From Similar Projects

The market splits into two camps; we close the loop in between:

- **Pure trackers** (ExpenseTitan, Expense_Manager, ZyPLJ/bookkeeping, Cloud-Ledger): record money only, no "time value" lens.
- **Pure real-time salary tools** (PayDance, realtime-salary-calculator, salary-timer, DevKitLab salary-ticker): tick the salary counter only, no expense tracking.
- **Us**: bookkeeping + hourly wage + work-hours conversion + scenario simulation — a "money ⇄ labor-time" loop; we then translate spending into "life sold", so you see the cost of being rented. Wage tickers celebrate earning; we count the days of your life you sold.
- **Truly offline**: many peers use Chart.js (CDN); charts break without internet. Ours is fully inline SVG, **zero external links, works offline**.
- **Single-file, zero dependency**: all CSS / JS / SVG inlined, double-click to run, no frameworks, no external APIs.

## Quick Start

Open `打工人小账本.html` in any modern browser. On mobile, deploy it as a web page and use "Share → Add to Home Screen" to use it like an app.

## Project Structure (Storage Convention)

```
dagongren-ledger/
├── 打工人小账本.html     # The only artifact: single-file app (zero-dep, fully inlined, truly offline)
├── README.md            # Chinese documentation
├── README_EN.md         # English documentation
├── LICENSE              # MIT
├── docs/
│   ├── ROADMAP.md       # Iteration roadmap (absorb from peers + our innovations)
│   ├── ARCHITECTURE.md  # Single-file architecture & rules
│   └── CHANGELOG.md     # Version history
└── assets/              # Preview screenshots / PWA icons (currently all inlined; placeholder)
```

Convention rules:

1. The app is always a single HTML file; new features are inlined into it. **No build step, no external CDN / framework.**
2. Versioning via Git Tag (e.g. `v1.0.0`) + GitHub Releases; record in `docs/CHANGELOG.md`.
3. Docs are bilingual; in-app copy is Chinese-first (target users), i18n may come later.
4. MIT license, consistent with mainstream peers, easy to share and fork.

## Data Safety & Privacy

Data lives only in your browser's localStorage, **never uploaded to any server**. Export a JSON backup often. Switching browsers / clearing cache loses data — back up regularly.

## Roadmap

See [docs/ROADMAP.md](docs/ROADMAP.md): absorb from mature peers (editable records, per-category budget overrun alerts, calendar view, category pie chart, custom categories, dark mode…) and innovate around "money ⇄ labor-time" (real-time wage widget, income-to-goods conversion, off-work countdown, overtime quantification…).

## Contributing

Forks / PRs welcome. Keep the "single-file, zero-dependency" architecture: inline all changes into `打工人小账本.html`.

## License

[MIT](LICENSE)
