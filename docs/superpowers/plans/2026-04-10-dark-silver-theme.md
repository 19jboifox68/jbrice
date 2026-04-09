# Dark & Silver Theme Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace every rose/red color instance in `index.html` with warm platinum silver (`#c9b99a` / `rgba(201,185,154,...)`).

**Architecture:** Three sequential edits to `index.html` — CSS config/variables first, then CSS body, then inline SVG and JavaScript. All changes are find-and-replace with no logic changes.

**Tech Stack:** Static HTML, Tailwind CSS (CDN config in `<script>`), custom CSS `<style>` block, inline JS canvas code.

---

## Files

- Modify: `c:/Users/Briceeey/OneDrive/Desktop/Portfolio Project/index.html`

## Color Reference

| Old | New | Usage |
|---|---|---|
| `#e11d48` | `#c9b99a` | Main accent hex |
| `#be123c` | `#b0a088` | Darker accent hex (hover states) |
| `#fb7185` | `#ddd0b8` | Light rose (work-tag text) |
| `#f43f5e` | `#c9b99a` | Medium rose (Asana brand color) |
| `rgba(225,29,72,X)` | `rgba(201,185,154,X)` | All opacity variants — preserve X |
| `%23e11d48` | `%23c9b99a` | URL-encoded hex in SVG |

---

### Task 1: Update CSS variables and Tailwind config

**Files:**
- Modify: `index.html` lines 29–30 (Tailwind config) and lines 47–48 (`:root` CSS variables) and line 80 (`::selection`)

- [ ] **Step 1: Update Tailwind config rose colors**

Lines 29–30. Change:
```js
500: '#e11d48',
600: '#be123c',
```
To:
```js
500: '#c9b99a',
600: '#b0a088',
```

- [ ] **Step 2: Update `--accent` CSS variable**

Line 47. Change:
```css
--accent: #e11d48;
```
To:
```css
--accent: #c9b99a;
```

- [ ] **Step 3: Update `--accent-glow` CSS variable**

Line 48. Change:
```css
--accent-glow: rgba(225, 29, 72, 0.18);
```
To:
```css
--accent-glow: rgba(201, 185, 154, 0.18);
```

- [ ] **Step 4: Update `::selection` background**

Line 80. Change:
```css
::selection { color: #fff; background-color: rgba(225, 29, 72, 0.25); }
```
To:
```css
::selection { color: #fff; background-color: rgba(201, 185, 154, 0.25); }
```

- [ ] **Step 5: Verify in browser**

Open `index.html`. Expected: heading text-accent spans, button, and nav active link now appear in warm gold/silver rather than red.

---

### Task 2: Replace all hardcoded red values in the CSS block

**Files:**
- Modify: `index.html` lines 105–1184

Make each edit individually using the Edit tool. For each, the surrounding context is given so the edit is unambiguous.

- [ ] **Step 1: Cursor horizontal arm box-shadow (line 105)**

Change:
```css
      box-shadow: 0 0 6px rgba(225,29,72,0.7);
      transition: width 0.2s cubic-bezier(0.34,1.56,0.64,1), background 0.2s ease, box-shadow 0.2s ease;
    }
    /* Vertical arm */
```
To:
```css
      box-shadow: 0 0 6px rgba(201,185,154,0.7);
      transition: width 0.2s cubic-bezier(0.34,1.56,0.64,1), background 0.2s ease, box-shadow 0.2s ease;
    }
    /* Vertical arm */
```

- [ ] **Step 2: Cursor vertical arm box-shadow (line 116)**

Change:
```css
      box-shadow: 0 0 6px rgba(225,29,72,0.7);
      transition: height 0.2s cubic-bezier(0.34,1.56,0.64,1), background 0.2s ease, box-shadow 0.2s ease;
```
To:
```css
      box-shadow: 0 0 6px rgba(201,185,154,0.7);
      transition: height 0.2s cubic-bezier(0.34,1.56,0.64,1), background 0.2s ease, box-shadow 0.2s ease;
```

- [ ] **Step 3: Cursor dot box-shadow (line 130)**

Change:
```css
      box-shadow: 0 0 8px rgba(225,29,72,0.9);
```
To:
```css
      box-shadow: 0 0 8px rgba(201,185,154,0.9);
```

- [ ] **Step 4: Cursor ring border (line 160)**

Change:
```css
      border: 1px solid rgba(225,29,72,0.45);
```
To:
```css
      border: 1px solid rgba(201,185,154,0.45);
```

- [ ] **Step 5: Cursor ring inner border-color (line 167)**

Change:
```css
      border-color: rgba(225,29,72,0.2);
```
To:
```css
      border-color: rgba(201,185,154,0.2);
```

- [ ] **Step 6: Hero glow background (line 299)**

Change:
```css
      background: radial-gradient(circle, rgba(225,29,72,0.08) 0%, transparent 70%);
```
To:
```css
      background: radial-gradient(circle, rgba(201,185,154,0.08) 0%, transparent 70%);
```

- [ ] **Step 7: Button hover background and box-shadow (lines 366, 368)**

Change:
```css
      background: #be123c;
      transform: translateY(-3px) scale(1.03);
      box-shadow: 0 12px 40px rgba(225,29,72,0.5), 0 0 0 1px rgba(225,29,72,0.3);
```
To:
```css
      background: #b0a088;
      transform: translateY(-3px) scale(1.03);
      box-shadow: 0 12px 40px rgba(201,185,154,0.5), 0 0 0 1px rgba(201,185,154,0.3);
```

- [ ] **Step 8: pulseGlow keyframes (lines 378–379)**

Change:
```css
      0%, 100% { box-shadow: 0 0 0 0 rgba(225,29,72,0); }
      50%       { box-shadow: 0 0 18px 6px rgba(225,29,72,0.35); }
```
To:
```css
      0%, 100% { box-shadow: 0 0 0 0 rgba(201,185,154,0); }
      50%       { box-shadow: 0 0 18px 6px rgba(201,185,154,0.35); }
```

- [ ] **Step 9: About photo rings (lines 480, 488)**

Change:
```css
      border: 1.5px dashed rgba(225,29,72,0.35);
```
To:
```css
      border: 1.5px dashed rgba(201,185,154,0.35);
```

Change:
```css
      border: 1px dashed rgba(225,29,72,0.15);
```
To:
```css
      border: 1px dashed rgba(201,185,154,0.15);
```

- [ ] **Step 10: Service card hover glow and border (lines 556, 561)**

Change:
```css
      background: radial-gradient(circle at 0% 0%, rgba(225,29,72,0.05) 0%, transparent 60%);
```
To:
```css
      background: radial-gradient(circle at 0% 0%, rgba(201,185,154,0.05) 0%, transparent 60%);
```

Change:
```css
      border-color: rgba(225,29,72,0.3);
```
To:
```css
      border-color: rgba(201,185,154,0.3);
```

- [ ] **Step 11: Service icon background and border (lines 569–570)**

Change:
```css
      background: rgba(225,29,72,0.1);
      border: 1px solid rgba(225,29,72,0.15);
```
To:
```css
      background: rgba(201,185,154,0.1);
      border: 1px solid rgba(201,185,154,0.15);
```

- [ ] **Step 12: Work card hover border (line 594)**

Change:
```css
      border-color: rgba(225,29,72,0.25);
```
To:
```css
      border-color: rgba(201,185,154,0.25);
```

- [ ] **Step 13: Work tag background, border, and text color (lines 632–633, 638)**

Change:
```css
      background: rgba(225,29,72,0.1);
      border: 1px solid rgba(225,29,72,0.15);
      border-radius: 100px;
      font-size: 0.68rem;
      font-weight: 600;
      letter-spacing: 0.05em;
      color: #fb7185;
```
To:
```css
      background: rgba(201,185,154,0.1);
      border: 1px solid rgba(201,185,154,0.15);
      border-radius: 100px;
      font-size: 0.68rem;
      font-weight: 600;
      letter-spacing: 0.05em;
      color: #ddd0b8;
```

- [ ] **Step 14: Contact section glow (line 676)**

Change:
```css
      background: radial-gradient(circle, rgba(225,29,72,0.06) 0%, transparent 70%);
```
To:
```css
      background: radial-gradient(circle, rgba(201,185,154,0.06) 0%, transparent 70%);
```

- [ ] **Step 15: Stack card hover border (line 725)**

Change:
```css
      border-color: rgba(225,29,72,0.3);
```
To:
```css
      border-color: rgba(201,185,154,0.3);
```

- [ ] **Step 16: Workflow nav button hover background (line 841)**

Change:
```css
      background: rgba(225,29,72,0.06);
    }
    .wf-slide {
```
To:
```css
      background: rgba(201,185,154,0.06);
    }
    .wf-slide {
```

- [ ] **Step 17: Workflow platform heading decorative lines (lines 904, 907)**

Change:
```css
      background: linear-gradient(to right, transparent, rgba(225,29,72,0.4));
    }
    .wf-platform-heading::after {
      background: linear-gradient(to left, transparent, rgba(225,29,72,0.4));
```
To:
```css
      background: linear-gradient(to right, transparent, rgba(201,185,154,0.4));
    }
    .wf-platform-heading::after {
      background: linear-gradient(to left, transparent, rgba(201,185,154,0.4));
```

- [ ] **Step 18: Workflow filter/tag button background (line 967)**

Change:
```css
      background: rgba(225,29,72,0.06);
    }
    .wf-empty-state {
      text-align: center;
      padding: 48px 24px;
      color: var(--text-muted);
      font-size: 0.88rem;
    }

    /* ── Project Modal ── */
```
To:
```css
      background: rgba(201,185,154,0.06);
    }
    .wf-empty-state {
      text-align: center;
      padding: 48px 24px;
      color: var(--text-muted);
      font-size: 0.88rem;
    }

    /* ── Project Modal ── */
```

- [ ] **Step 19: Project modal tag background (line 1115)**

Change:
```css
      background: rgba(225,29,72,0.06);
      white-space: nowrap;
```
To:
```css
      background: rgba(201,185,154,0.06);
      white-space: nowrap;
```

- [ ] **Step 20: Workflow filter button hover border and active states (lines 1178, 1184)**

Change:
```css
      border-color: rgba(225,29,72,0.4);
```
To:
```css
      border-color: rgba(201,185,154,0.4);
```

Change:
```css
      background: rgba(225,29,72,0.07);
```
To:
```css
      background: rgba(201,185,154,0.07);
```

- [ ] **Step 21: Verify in browser**

Expected: All hover effects, glows, rings, and borders now glow silver/gold instead of red. Button hover is warm silver. Service icons are silver-tinted.

---

### Task 3: Replace colors in inline SVG and JavaScript

**Files:**
- Modify: `index.html` lines ~1484, 1969–2005, 2260, 2268–2269, 2350, 2360

- [ ] **Step 1: Replace URL-encoded SVG color (line ~1484)**

Find the inline `<div>` with the SVG background-image pattern. It contains multiple occurrences of `%23e11d48`. Replace all of them with `%23c9b99a`.

The string to find (beginning of the relevant attribute):
```
stroke='%23e11d48' stroke-width='0.8' fill='none'/%3E%3Ccircle cx='60' cy='60' r='4' fill='none' stroke='%23e11d48' stroke-width='0.8'/%3E%3Ccircle cx='60' cy='60' r='1.5' fill='%23e11d48'/%3E%3Cpath d='M0 20 H20 V0' stroke='%23e11d48' stroke-width='0.5' fill='none'/%3E%3Ccircle cx='20' cy='20' r='1.2' fill='%23e11d48'/%3E%3Cpath d='M120 100 H100 V120' stroke='%23e11d48' stroke-width='0.5' fill='none'/%3E%3Ccircle cx='100' cy='100' r='1.2' fill='%23e11d48'/%3E%3Cpath d='M0 90 H30' stroke='%23e11d48' stroke-width='0.4' fill='none'/%3E%3Ccircle cx='30' cy='90' r='1' fill='%23e11d48'/%3E%3Cpath d='M90 0 V30' stroke='%23e11d48' stroke-width='0.4' fill='none'/%3E%3Ccircle cx='90' cy='30' r='1' fill='%23e11d48'
```
Replace `%23e11d48` with `%23c9b99a` throughout that line (use `replace_all: true` on the Edit tool with `%23e11d48` → `%23c9b99a`).

- [ ] **Step 2: Replace canvas hero star/line JS colors (lines ~1969–2005)**

Change:
```js
            ctx.strokeStyle = `rgba(225,29,72,${lineOpacity})`;
```
To:
```js
            ctx.strokeStyle = `rgba(201,185,154,${lineOpacity})`;
```

Change:
```js
              ctx.fillStyle = `rgba(225,29,72,${lineOpacity * 3})`;
```
To:
```js
              ctx.fillStyle = `rgba(201,185,154,${lineOpacity * 3})`;
```

Change:
```js
            ctx.fillStyle = `rgba(225,29,72,${op})`;
            const g = ctx.createRadialGradient(x, y, 0, x, y, r);
            g.addColorStop(0, `rgba(225,29,72,${op * 0.4})`);
```
To:
```js
            ctx.fillStyle = `rgba(201,185,154,${op})`;
            const g = ctx.createRadialGradient(x, y, 0, x, y, r);
            g.addColorStop(0, `rgba(201,185,154,${op * 0.4})`);
```

Change (the standalone fillStyle after addColorStop):
```js
            ctx.fillStyle = `rgba(225,29,72,${op})`;
```
To:
```js
            ctx.fillStyle = `rgba(201,185,154,${op})`;
```

Note: There are two `ctx.fillStyle = \`rgba(225,29,72,${op})\`` lines (~1995 and ~2005). Confirm both are changed.

- [ ] **Step 3: Replace workflow card JS color values (lines ~2260, 2268–2269)**

Change:
```js
        { label: 'n8n',         color: '#e11d48' },
```
To:
```js
        { label: 'n8n',         color: '#c9b99a' },
```

Change:
```js
        { label: 'Pinecone',    color: '#e11d48' },
        { label: 'Asana',       color: '#f43f5e' },
```
To:
```js
        { label: 'Pinecone',    color: '#c9b99a' },
        { label: 'Asana',       color: '#c9b99a' },
```

- [ ] **Step 4: Replace network canvas JS colors (lines ~2350, 2360)**

Change:
```js
        ctx.strokeStyle = `rgba(225,29,72,${opacity})`;
```
To:
```js
        ctx.strokeStyle = `rgba(201,185,154,${opacity})`;
```

Change:
```js
        ctx.fillStyle = `rgba(225,29,72,${opacity * 2})`;
```
To:
```js
        ctx.fillStyle = `rgba(201,185,154,${opacity * 2})`;
```

- [ ] **Step 5: Verify in browser**

Open `index.html`. Expected: Hero canvas particles and connection lines glow silver. Background SVG pattern dots are silver. Workflow platform tag dots are silver/gold. No red/rose anywhere on the page.
