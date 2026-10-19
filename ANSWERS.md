# ANSWERS.md — IT 120 Flutter Lab (Architecture, Widgets, and Basic UI)

**Student:** Andy Mark L. Crasco  
**Section:** ILGX3  
**Course:** IT 120 Integrative Programming and Technologies 2  
**Date:** October 19, 2026

---

## GitHub Repository Link
https://github.com/YOUR_USERNAME/flutter_basics_lab

---

## Activity 2 — Debug Console Lines

Paste the last three `build() called:` lines from VS Code's Debug Console here:

```
build() called: 0 glasses
build() called: 1 glasses
build() called: 2 glasses
```

*(Note: Replace the lines above with the actual output from your Debug Console after tapping "+" three times.)*

---

## Experiment Observations

### Activity 2 — Moving `_glasses++` outside `setState()`
When `_glasses++` is placed outside `setState()`, the variable changes in memory but Flutter does not rebuild the UI. The screen does not update even though you tap "+". This proves that `setState()` is required to notify Flutter that data changed so `build()` can be called again.

### Activity 3 — Removing `Expanded` from a StatBox
Without `Expanded`, that StatBox sizes to its content instead of sharing the row equally. The three boxes become unequal width, and on narrow screens the row may overflow (yellow and black stripes). `Expanded` makes each child fill all remaining space so the boxes share the row equally regardless of screen width.

### Activity 5 — Changing `buildTheme()` (button corner radius 8 → 20)
Changing `borderRadius` from 8 to 20 made every `ElevatedButton` in the app more rounded (pill-shaped). This shows that `ThemeData` styles the whole app at once, not just one widget.

---

## Review Questions

### 1. Difference between StatelessWidget and StatefulWidget?
- **StatelessWidget:** Never changes after it is drawn. Configuration is fixed. Example from this lab: `ProfileCard` (Activity 1).
- **StatefulWidget:** Can change while the app runs — it holds mutable state. Example: `WaterTrackerPage` (Activity 2).

### 2. Why is a StatefulWidget written as two classes?
- The `StatefulWidget` class only creates its `State` object via `createState()`; it has no `build()` of its own.
- The `State` class (e.g., `_WaterTrackerPageState`) keeps the data that changes and contains `build()`. `setState()` tells Flutter the data changed so `build()` runs again.

### 3. Activity 2 — What happened when you changed `_glasses` outside `setState()`?
The variable changed, but Flutter was not notified, so `build()` was not called and the screen did not update. The tap appeared to do nothing.

### 4. When is `build()` called?
Every time `setState()` is invoked — after each tap on "+", "–", or "Reset". The Debug Console shows a new `build() called` line each time.

### 5. Main axis vs cross axis of Row and Column?
- **Row:** main axis is horizontal, cross axis is vertical.
- **Column:** main axis is vertical, cross axis is horizontal.
- `MainAxisAlignment` positions children along the main axis; `CrossAxisAlignment` positions them along the cross axis.

### 6. Activity 3 — What happened when you removed `Expanded` from a StatBox?
That box no longer takes an equal share of the row; it shrinks to fit its content, so boxes become unequal and may overflow (yellow/black stripes). `Expanded` makes a child fill all remaining space so boxes share the row equally.

### 7. Why use `GridView.builder` instead of a `Column` with many children?
`GridView.builder` is scrollable and creates only visible items (lazy loading), so long lists stay fast. A `Column` builds all children at once and is not scrollable by default, so it would overflow the screen.

### 8. How do Stack and Positioned create the Best seller badge?
`Stack` draws children on top of each other (first child at the bottom). `Positioned` pins a child with `top`, `bottom`, `left`, or `right` distances. The badge is pinned to the top-left corner, layered above the card's icon/name/price.

### 9. Difference between customizing with ThemeData and a style on one widget?
- **ThemeData:** Styles the whole app at once. Example: `elevatedButtonTheme` rounds all `ElevatedButton` corners.
- **Style on one widget:** Affects only that widget. Example: `TextStyle(fontSize: 24, ...)` on a single `Text`.

### 10. Dark-mode switch — which widget holds state, and how does the change reach MaterialApp?
`_ThemeDemoAppState` holds the `_isDark` state. `_setDark` changes it inside `setState()`, which rebuilds `MaterialApp` with `themeMode` set to `ThemeMode.dark` or `ThemeMode.light`, and the change reaches the whole app.

---

## Checklist Before Submission
- [x] studentName and studentId filled in with your own details
- [x] All five activities run without errors
- [x] All seven screenshots are in the screenshots folder and show your name
- [x] Each activity's "Your task" is done
- [x] ANSWERS.md has your GitHub link, Debug Console lines, observations, and all ten answers
- [ ] Project is pushed to GitHub
- [ ] ZIP file is named `SECTION_LASTNAME_FIRSTNAME.zip`
