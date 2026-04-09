# Color Theme — Silver Accent Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace every sandy gold accent (`#c9b99a` / `rgba(201,185,154,…)`) with soft silver (`#d4d4d4` / `rgba(212,212,212,…)`) throughout the portfolio site.

**Architecture:** All changes are find-and-replace operations inside a single file (`index.html`). There are 4 distinct string patterns to swap. No structural changes needed.

**Tech Stack:** Plain HTML/CSS, Tailwind CDN, vanilla JS canvas

---

### Task 1: Replace CSS variable `--accent`

**Files:**
- Modify: `index.html:43`

- [ ] **Step 1: Replace the variable value**

In `index.html` line 43, change:
```css
--accent: #c9b99a;
```
to:
```css
--accent: #d4d4d4;
```

- [ ] **Step 2: Verify**

Open `index.html` in a browser. The cursor cross arms, badge dot, and button background should all appear silver/light-grey instead of sandy beige.

---

### Task 2: Replace CSS variable `--accent-glow`

**Files:**
- Modify: `index.html:44`

- [ ] **Step 1: Replace the variable value**

In `index.html` line 44, change:
```css
--accent-glow: rgba(201, 185, 154, 0.18);
```
to:
```css
--accent-glow: rgba(212, 212, 212, 0.18);
```

---

### Task 3: Replace all spaced `rgba(201, 185, 154, …)` inline values

**Files:**
- Modify: `index.html` (lines 76, 313, 314)

These use spaces after commas.

- [ ] **Step 1: Replace all three occurrences**

Find every instance of `rgba(201, 185, 154,` and replace with `rgba(212, 212, 212,`. Affected lines:

| Line | Before | After |
|------|--------|-------|
| 76 | `rgba(201, 185, 154, 0.25)` | `rgba(212, 212, 212, 0.25)` |
| 313 | `rgba(201, 185, 154, 0.08)` | `rgba(212, 212, 212, 0.08)` |
| 314 | `rgba(201, 185, 154, 0.2)` | `rgba(212, 212, 212, 0.2)` |

---

### Task 4: Replace all compact `rgba(201,185,154,…)` inline values

**Files:**
- Modify: `index.html` (lines 101, 112, 126, 156, 163, 295, 364, 374, 375, 476, 484, 552, 557, 565, 566, 590, 628, 629, 634 area, 672, 721, 837, 900, 903, 963, 1111, 1174, 1180, 1965, 1977, 1991, 1994, 2001, 2346, 2356)

These use no spaces after commas.

- [ ] **Step 1: Global replace**

Find every instance of `rgba(201,185,154,` and replace with `rgba(212,212,212,`. This covers all remaining canvas JS and CSS inline uses in one pass.

---

### Task 5: Replace hardcoded hex `#c9b99a` in JS

**Files:**
- Modify: `index.html` (lines 2256, 2264, 2265)

- [ ] **Step 1: Replace hex values**

Find every remaining instance of `#c9b99a` (outside the `:root` block already fixed in Task 1) and replace with `#d4d4d4`.

Affected lines are inside the skills/tools chart data:
```js
{ label: 'n8n',      color: '#c9b99a' },  // → '#d4d4d4'
{ label: 'Pinecone', color: '#c9b99a' },  // → '#d4d4d4'
{ label: 'Asana',    color: '#c9b99a' },  // → '#d4d4d4'
```

---

### Task 6: Replace badge/tag text color `#ddd0b8`

**Files:**
- Modify: `index.html` (lines 319, 634)

- [ ] **Step 1: Replace the color**

Find every instance of `#ddd0b8` and replace with `#c8c8c8`.

---

### Task 7: Final visual check

- [ ] **Step 1: Open in browser**

Open `index.html` in a browser and verify:
- Cursor cross arms are silver, not sandy beige
- Availability badge dot and border are silver
- Primary button is silver/light-grey
- Hero glow and canvas particles are neutral grey
- Skills chart bars for n8n, Pinecone, Asana are silver
- No warm sandy/gold tones remain anywhere on the page

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "style: replace sandy gold accent with soft silver (#d4d4d4)"
```
