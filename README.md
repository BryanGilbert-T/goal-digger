# Goal Digger — Flutter App

An AI-driven productivity app that converts big goals into bite-sized micro-tasks
with **Adaptive Task Suggestions (ATS)** that responds to mood, energy,
goal importance, and deadlines in real-time.

## Architecture

The app is built around a single **ATS (Adaptive Task Suggestions)** engine that:

1. Reads your **goals** (with importance 1–5 + deadline date)
2. Reads your **current energy/mood**
3. Generates today's **task list** (Task page)
4. Distributes all sub-tasks across the **calendar** (Calendar page)
5. Re-prioritizes in real-time when energy or goals change
6. Allows **swapping** any undone task with a higher-priority one from another day
7. Allows **adding** more tasks when today's are all done

## Project Structure

```
flutter_project/
├── lib/
│   ├── main.dart                    # App entry
│   ├── models/
│   │   ├── sub_task.dart            # SubTask (belongs to a Goal)
│   │   ├── goal_item.dart           # Goal with importance, deadline, subtasks
│   │   └── pet_look.dart            # Pet skin definitions
│   ├── state/
│   │   └── app_state.dart           # AppState + ATS engine + global reminder
│   ├── theme/
│   │   ├── colors.dart
│   │   └── text_styles.dart
│   ├── widgets/
│   │   ├── ambient_background.dart
│   │   ├── bottom_nav.dart
│   │   ├── glass_card.dart
│   │   ├── profile_button.dart
│   │   └── settings_button.dart
│   └── screens/
│       ├── shell.dart               # App shell + GLOBAL reminder overlay
│       ├── planner_screen.dart      # ATS card + Energy Matcher + Goals + Goal Deconstructor
│       ├── task_screen.dart         # Today's ATS-generated tasks + swap + add buttons
│       ├── calendar_screen.dart     # Full month with ALL subtasks distributed
│       ├── community_screen.dart    # Leaderboard, friends, finder, team challenge
│       └── companion_screen.dart    # Pet, hunger, feed-by-tasks, wallet, shop
└── pubspec.yaml
```

## Tabs Overview

| Tab        | Contents |
|------------|----------|
| **Planner** | **Adaptive Task Suggestions** card (with embedded Energy Matcher), goals list with importance (1–5) & deadline sliders, Goal Deconstructor, test reminder trigger |
| **Task** | Progress orb, Goal Tracker, **today's ATS-generated tasks** with Focus Mode, **↻ Swap** any undone task, **+ Add another** task from upcoming days when all done |
| **Calendar** | Full month grid showing **all sub-tasks distributed** across days (color-coded per goal), deadline markers, today highlight, selected day detail |
| **Community** | Weekly leaderboard, friends with cheer, Community Finder (compatibility %), Team challenge |
| **Companion** | Active pet with skins, **Feed It!** gamification (hunger meter, feed only via completed tasks), wallet, shop |

## Key Behaviors

### Adaptive Task Suggestions Engine
Located in `app_state.dart` → `_computeAdaptiveSuggestions()`. Scores each undone subtask by:

```
score = (goal.importance × 2)
      + (10 / daysUntilDeadline)        // urgency
      + dayMatch                         // prefers today's scheduled tasks
      + energyMatch                      // light/focus/stretch vs energy
```

Top N tasks are picked (N = 2 for low energy, 4 for steady, 5 for high).

### Real-Time Re-prioritization
Changing your mood/energy or any goal's importance/deadline immediately re-runs ATS and updates Today's tasks (already-completed tasks stay in the list).

### Global Reminders
Triggered from anywhere (`state.showReminder(...)`), the reminder is rendered as a full-screen overlay in `shell.dart`, regardless of which tab is active.

## Setup

```bash
cd flutter_project
flutter pub get
flutter run -d chrome      # or ios / android / macos
```

## Pending Flutter Updates

The React preview now includes the following features (to port to Flutter, mirror these changes in `state/app_state.dart` + corresponding screens):

- **Profile overlay** (tap profile button) with avatar, stats grid, plan, achievements, edit/logout — see `ProfileOverlay` in `src/App.tsx`. In Flutter, render a `Dialog`/full-screen `Stack` overlay from `shell.dart`.
- **Settings overlay** (tap gear icon) with grouped toggles (notifications, sound, dark mode, kind mode, daily reminder) and account row — see `SettingsOverlay`. In Flutter use `SwitchListTile` inside a modal.
- **Auth flow** (login + signup) with email/password fields, toggle between modes, social-login buttons.
- **Date picker overlay** with month/year navigation + grid + month/year picker mode — already available in Flutter via `showDatePicker(...)` (Material).
- **Goal model** changed `deadlineDay: int` → `deadline: DateTime` and added `category: String` ("Career", "Study", etc.). Subtasks changed `scheduledDay: int` → `scheduledDate: DateTime`.
- **Calendar** uses month nav (`viewYear`, `viewMonth`) instead of single-month constant. Removed "Scheduled sub-tasks" right panel.
- **Planner ATS card** removed energy-chip row and "Generated for today" preview — only mood emoji buttons remain.
- **Planner "Your goals"** redesigned as `GoalCard` with: gradient strip, category chip, star-button row (1–5) for "Interest & priority", deadline picker button + ± day quick-buttons.
- **Goal Deconstructor** uses category chips, star buttons, and deadline button (with quick +3/+7/+14/+30 day chips) instead of sliders.
- **Task page Goal Tracker** redesigned with gradient accent strips, urgency badges (`urgent`/`soon`/`ok`), per-subtask dots row.
- **Task page** "All done" card now prominently shows the **+ Add another** button when more tasks are available across upcoming days.

## Dependencies

| Package         | Purpose            |
|-----------------|--------------------|
| provider        | State management   |
| google_fonts    | Inter font         |
| flutter_animate | Animations (opt.)  |
