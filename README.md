# Procrastination Breaker

A lightweight focus timer built for the **Toggle Wars 2026** hackathon (**Track 1: Test Something Real**), powered by **Flagsmith Experimentation** to test how task framing affects whether people actually start and stick with a work session.

**Live Demo:** https://kawaresrushti.github.io/Procrastination-Breaker/

---

## Hypothesis

Framing the focus button as a **2-minute micro-sprint** instead of a **25-minute Pomodoro** will increase **60-second sprint completions** by at least **20%** within 4 days.

---

## Flagsmith Experiment Setup

| Setting | Configuration |
| :--- | :--- |
| **Experiment Name** | Micro-Sprint vs Pomodoro Framing |
| **Feature Flag** | `sprint_framing` (Multivariate) |
| **Control (50%)** | `pomodoro_25` — Deep Focus Mode (25-minute Pomodoro) |
| **Variant_1 (50%)** | `micro_2` — Micro-Sprint Mode (2-minute micro-sprint) |
| **Rollout** | 100% of visitors |
| **Primary Metric** | `sprint_60s_completed` (Occurrence, higher is better) |
| **Secondary Event** | `sprint_started` |

---

## How It Works

1. Each visitor receives a persistent anonymous ID in `localStorage` so Flagsmith consistently assigns them to one variant and links exposure to conversion.
2. The app initializes `@flagsmith/flagsmith` in the browser with `enableEvents: true` and evaluates `sprint_framing` via `getExperimentFlag()`.
3. Visitors see either **Deep Focus Mode** (`pomodoro_25`) or **Micro-Sprint Mode** (`micro_2`).
4. When a visitor starts the timer and stays active for **60 seconds**, the app fires and flushes the `sprint_60s_completed` conversion event to Flagsmith's Managed Warehouse.

---

## Tech Stack

- **Frontend:** Single-file `index.html` (HTML, CSS, Vanilla JS)
- **Feature Flags & A/B Testing:** Flagsmith Cloud (`@flagsmith/flagsmith` ES module via `esm.sh`)
- **Hosting:** GitHub Pages

---

## Experiment Results

> *Experiment currently live — final conversion rates, Flagsmith results screenshot, and takeaways will be added before submission.*
