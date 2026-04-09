# About Section — Compact Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the full-height About section in `index.html` with a compact side-by-side layout that reduces vertical footprint while preserving all content and visual identity.

**Architecture:** Three targeted edits to `index.html` — CSS photo sizing, section/grid spacing classes, and bio paragraph HTML. No new files. No JS changes.

**Tech Stack:** Static HTML, Tailwind CSS (CDN), custom CSS in `<style>` block inside `index.html`

---

## Files

- Modify: `index.html:455–506` — CSS `.about-photo`, `.about-photo-ring`, `.about-photo-ring-2` sizing
- Modify: `index.html:1313–1381` — About section HTML (spacing classes + bio paragraphs)

---

### Task 1: Scale down photo and rings via CSS

The photo currently fills the full column (`width: 100%; aspect-ratio: 4/5`). Constrain it to ~200px wide by adding a `max-width` to the `.about-photo-wrap`, and adjust ring insets proportionally.

**Files:**
- Modify: `index.html:468–506` (`.about-photo-wrap`, `.about-photo-ring`, `.about-photo-ring-2`, `.about-photo` CSS)

- [ ] **Step 1: Update `.about-photo-wrap` CSS**

In the `<style>` block, locate `.about-photo-wrap` (line ~468) and add `max-width: 200px;`:

```css
.about-photo-wrap {
  position: relative;
  width: 100%;
  max-width: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: photoFloat 6s ease-in-out infinite;
}
```

- [ ] **Step 2: Update `.about-photo-ring` inset**

Scale the inner ring inset from `-18px` down to `-10px` to match the smaller photo:

```css
.about-photo-ring {
  position: absolute;
  inset: -10px;
  border-radius: 16px;
  border: 1.5px dashed rgba(225,29,72,0.35);
  animation: ringRotate 12s linear infinite;
  pointer-events: none;
}
```

- [ ] **Step 3: Update `.about-photo-ring-2` inset**

Scale the outer ring inset from `-32px` down to `-20px`:

```css
.about-photo-ring-2 {
  position: absolute;
  inset: -20px;
  border-radius: 20px;
  border: 1px dashed rgba(225,29,72,0.15);
  animation: ringRotateReverse 20s linear infinite;
  pointer-events: none;
}
```

- [ ] **Step 4: Verify in browser**

Open `index.html` in a browser (or live server). Scroll to the About section.
Expected: Photo is visibly smaller (~200px wide), both rings are visible and proportional, floating animation still works, no ring overflow clipping.

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: scale down about photo and rings to compact size"
```

---

### Task 2: Reduce section and grid spacing

Reduce section vertical padding and column gap to tighten the overall section height.

**Files:**
- Modify: `index.html:1313–1315` (section and grid classes)

- [ ] **Step 1: Update section padding class**

Line ~1313 — change `py-28` to `py-16`:

```html
<section id="about" class="py-16">
```

- [ ] **Step 2: Update grid gap class**

Line ~1315 — change `gap-16` to `gap-12`:

```html
<div class="grid md:grid-cols-2 gap-12 items-center">
```

- [ ] **Step 3: Verify in browser**

Expected: The About section is noticeably shorter top-to-bottom. The two columns are slightly closer together but not cramped.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: reduce about section padding and column gap"
```

---

### Task 3: Tighten internal bio spacing

Reduce the margin between bio text, tool tags, and the CTA button.

**Files:**
- Modify: `index.html:1340` (bio wrapper div)
- Modify: `index.html:1356` (tool tags div)

- [ ] **Step 1: Update bio wrapper spacing**

Line ~1340 — change `space-y-4 mb-8` to `space-y-3 mb-4`:

```html
<div class="reveal reveal-delay-2 space-y-3 mb-4" style="color:var(--text-muted);line-height:1.8;font-weight:300;">
```

- [ ] **Step 2: Update tool tags bottom margin**

Line ~1356 — change `mb-8` to `mb-4`:

```html
<div class="reveal reveal-delay-3 flex flex-wrap gap-2 mb-4">
```

- [ ] **Step 3: Verify in browser**

Expected: Bio paragraphs, tag cloud, and button are visually tighter — no large empty gaps between them.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: tighten about section internal spacing"
```

---

### Task 4: Condense bio from 3 paragraphs to 2

Merge paragraphs 1 and 2 into a single paragraph. Keep paragraph 3 (the "8+ years" one) unchanged.

**Files:**
- Modify: `index.html:1341–1353`

- [ ] **Step 1: Replace the three `<p>` tags with two**

Replace the entire bio content inside the wrapper div with:

```html
<p>
  I'm <span style="color:var(--text-primary);font-weight:500;">James Brice Arda</span> — an AI automation specialist who turns complex, time-consuming processes into sleek, self-running systems. Whether it's wiring up tools like n8n, Make.com and Zapier, or deploying custom AI agents, I build end-to-end pipelines — from lead generation and CRM integration to AI-powered content creation and intelligent knowledge bases.
</p>
<p>
  With <span style="color:var(--text-primary);font-weight:500;">8+ years in customer service</span>, I understand the real pain behind repetitive tasks — which is why I build automation that actually solves the problem, not just patches it.
</p>
```

- [ ] **Step 2: Verify in browser**

Expected: Two paragraphs in the bio. First paragraph covers intro + tools + pipelines. Second paragraph is the customer service line. No third paragraph.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: condense about bio from 3 paragraphs to 2"
```
