# 🪵 Schepki Extensions — Dashboard

> **Micro-SaaS Empire** | Developer: [Nikol Dev Tools](https://buymeacoffee.com/nikoltools) | Analytics: GA4 `G-3ZKRBK0TBV`

---

## 📊 Extensions Tracker

| # | Extension | What it does | Geo | Store | Status | Monetization | Notes |
|---|---|---|---|---|---|---|---|
| 1 | **Pomodoro Timer** | Focus timer using the Pomodoro technique | 🇺🇸 US / Global | Chrome Web Store | 🟡 In Review | [Buy Me a Coffee](https://buymeacoffee.com/nikoltools) | GA4 ✅ Remote Config ✅ |
| 2 | **Breathing Timer** | Breathing exercise timer (4-7-8 technique) | 🇺🇸 US / Global | Chrome Web Store | 🟡 In Review | [Buy Me a Coffee](https://buymeacoffee.com/nikoltools) | GA4 ✅ Remote Config ✅ |
| 3 | *Tab Limiter* | Limits number of open tabs for focus | 🇺🇸 US / Global | Chrome Web Store | ⚪ Planned | Buy Me a Coffee | — |
| 4 | *Quick Notes* | Quick notes on new tab page | 🇺🇸 US / Global | Chrome Web Store | ⚪ Planned | Buy Me a Coffee | — |

### Status Legend

| Icon | Meaning |
|---|---|
| 🟢 | **Live** — published and available to users |
| 🟡 | **In Review** — submitted, awaiting store approval |
| 🔵 | **In Development** — code being written / tested locally |
| ⚪ | **Planned** — idea confirmed, development not started |
| 🔴 | **Rejected** — failed moderation, needs fixes |

---

## 🏗️ Infrastructure

| Component | Details |
|---|---|
| **Remote Config** | `config.json` in this repo — controls all links across all extensions |
| **Analytics** | Google Analytics 4 — Measurement ID: `G-3ZKRBK0TBV` |
| **Donations** | Stripe → [buymeacoffee.com/nikoltools](https://buymeacoffee.com/nikoltools) |
| **Privacy Policy** | [nikol-dev-tools.github.io/schepki-config/privacy.html](https://nikol-dev-tools.github.io/schepki-config/privacy.html) |
| **Boilerplate** | [github.com/nikol-dev-tools/schepki-boilerplate](https://github.com/nikol-dev-tools/schepki-boilerplate) |

---

## ⚙️ How to update Remote Config

1. Open `config.json` in this repository
2. Click the **pencil icon** (Edit) in the top right
3. Change the value you need (e.g., update the donation link)
4. Click **"Commit changes"** (green button)

All extensions will pick up the new values within minutes — no store resubmission needed.

---

## 📁 Files in this repo

| File | Purpose |
|---|---|
| `config.json` | Remote Config — all links and settings for all extensions |
| `index.html` | Landing page (hosted on GitHub Pages) |
| `privacy.html` | Privacy Policy page (required by Chrome Web Store) |
