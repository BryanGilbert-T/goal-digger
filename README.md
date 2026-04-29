# 🌱 Goal Digger — Product Overview

> *Stop planning. Start digging.*

Goal Digger is an AI-powered productivity companion that turns overwhelming goals into small, honest daily actions — and adapts to your real life when it changes.

---

## What is Goal Digger?

Most productivity apps expect you to show up perfectly every day. Goal Digger doesn't. It meets you where you are — tired, busy, or behind — and quietly rebuilds your day around what actually matters, without guilt or punishment.

You tell it your goals. It figures out the steps, schedules them across your calendar, reads your mood, and gives you the next right action to take. That's it. No endless setup, no overwhelming task lists.

---

## The Problem It Solves

People set goals but lose momentum because:

- Planning is exhausting and takes longer than doing
- Task lists don't adapt when life gets in the way
- Missing a day feels like failing, so people give up
- There is no one to check in with, celebrate small wins, or offer a nudge

Goal Digger solves each of these directly.

---

## Core Philosophy

| Principle | How it shows up |
|---|---|
| **Bite-sized actions** | Every goal is broken into micro-tasks of 5–25 minutes |
| **Mood-aware scheduling** | Tap your mood and the daily plan reshapes in real time |
| **No punishment** | Deadline pressure is detected; the app adjusts, not accuses |
| **Urgency-first** | The AI scores tasks by importance × deadline × energy match |
| **Friendly accountability** | A companion pet, friends, and communities keep you going |

---

## The 5 Screens

### 🏠 Home
The starting point. Your AI companion pet lives here. Tell it your goal — it breaks it down into steps using a conversational chat, assigns each step to a day on your calendar, and shows you your active goals with sliders for priority and deadline.

### ✅ Task
Your daily plan, built by the AI based on your goals, deadlines, and today's mood. Tap any task to see a short guide on how to actually start it. Swap a task if you'd rather do something else. Add more when you've finished everything. Each completed task feeds your pet and earns coins.

### 🗓️ Calendar
Your full month view, populated automatically with every step from every goal. Routines appear differently from tasks so you can tell them apart at a glance. Tap any day to see a view-only preview of what's scheduled. Add recurring routines as reminders, not as more tasks to complete.

### 👥 Community
Find people working on similar goals. Add friends, join or create groups, see a weekly kind-mode leaderboard. The Community Finder suggests groups based on what role they're missing — if a team needs a designer and you're building a portfolio, you'll see it.

### 🛍️ Customize Pet
Spend coins earned from completing tasks on costumes, furniture, and accessories for your companion. Your pet's appearance syncs across every page of the app.

---

## The AI Engine (ATS — Adaptive Task Suggestions)

Goal Digger uses a scoring algorithm to decide which tasks appear in your daily list:

```
score = (goal importance × 2)
      + (10 ÷ days until deadline)      ← urgency
      + day match bonus                  ← prefers today's scheduled tasks
      + energy match                     ← light/focus/stretch vs your mood
```

**Mood guard:** If you say you're tired but a deadline is tomorrow with 3+ tasks remaining, the system keeps those tasks and gently softens the approach instead of removing them.

**Slot count adapts to energy:**
- 😔 Tired → 2 tasks
- 😐 Okay → 4 tasks
- 😊 Great → 5 tasks

---

## Companion Pet System

Your pet is more than decoration. It:

- **Grows hungrier** if you don't complete tasks (each task completion raises pet energy by 15%)
- **Earns you coins** — every completed task is worth points redeemable in the pet shop
- **Syncs to your chosen skin** — Mint, Peach, or Lunar — across every page of the app
- **Lives on the Home screen** and the navigation bar so it's always with you

Feeding the pet costs 10 coins and requires you to have earned at least 10 points from tasks first. You can't buy your way to a happy pet — you have to do the work.

---

## Routines vs Tasks

| | Tasks | Routines |
|---|---|---|
| Source | Created from goals via AI | Created manually |
| Purpose | Move a goal forward | Remind you of habits |
| Completable | Yes, earns points | No, reminder only |
| Calendar | Yes, scheduled per day | Yes, shown with dashed amber style |
| Frequency | Assigned per step | Daily, Weekly, Monthly, Once, Custom |

---

## Who It's For

Goal Digger is designed for anyone who:

- Sets goals but struggles with follow-through
- Experiences procrastination or inconsistency
- Has tried productivity apps but abandoned them
- Wants accountability without shame
- Is a student, freelancer, career-changer, or anyone building something on the side

---

## Tech Stack

| Layer | Web | Mobile |
|---|---|---|
| Framework | React 19 + Vite | Flutter 3 |
| Styling | Tailwind CSS v4 | Custom theme + Google Fonts |
| State | React useState / useCallback | Provider (ChangeNotifier) |
| Charts | SVG (inline) | CustomPaint |
| Navigation | Tab-based (5 tabs) | Bottom nav bar |
| Platform | Browser (PWA-ready) | iOS + Android + Web |

---

## Design Language

- **Warm off-white background** (`#F7F1E8`) — feels like paper, not a screen
- **Frosted glass cards** — depth without heaviness
- **Ambient gradient blobs** — alive, breathing, never static
- **One unified pet character** — reused across all pages, reflects your skin choice
- **No punitive red states** — overdue feels gentle amber, not alarming red
- **Dark nav pill** — the active tab is always clear

---

## Current Version

- Version: `1.0.0`
- Status: Prototype / MVP
- Web preview: React + Vite (see `README.md in branch web-version`)
- Mobile source: Flutter (see `README.md in branch app-version`)
