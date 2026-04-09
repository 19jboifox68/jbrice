# Discovery Call CTA Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the "Send me a message" mailto button with a "Book a discovery call" Google Calendar link, and update the contact section description to match.

**Architecture:** Two HTML edits inside `index.html` — the description paragraph text and the primary CTA anchor element. No CSS or JS changes required.

**Tech Stack:** Vanilla HTML (single file, no build step)

---

### Task 1: Update contact section description and CTA button

**Files:**
- Modify: `index.html:1735-1745`

- [ ] **Step 1: Update the description paragraph**

In `index.html`, find the paragraph at lines 1735–1738:

```html
      <p class="reveal reveal-delay-2 mb-10 mx-auto" style="color:var(--text-muted);font-weight:300;line-height:1.8;max-width:460px;">
        Have a process you want to automate? A workflow that's costing your team hours
        every week? Let's talk — I'll build the system that fixes it.
      </p>
```

Replace with:

```html
      <p class="reveal reveal-delay-2 mb-10 mx-auto" style="color:var(--text-muted);font-weight:300;line-height:1.8;max-width:460px;">
        Have a process you want to automate? A workflow that's costing your team hours
        every week? Book a free 30-minute discovery call — I'll map out exactly how to fix it.
      </p>
```

- [ ] **Step 2: Replace the primary CTA button**

In `index.html`, find the anchor at lines 1741–1744:

```html
        <a href="mailto:hello@brice.dev" class="btn-primary" style="font-size:0.95rem;padding:15px 36px;">
          Send me a message
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8h12M9 3l5 5-5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </a>
```

Replace with:

```html
        <a href="https://calendar.app.google/mqn9R7rEz5u25Q8r8" target="_blank" rel="noopener noreferrer" class="btn-primary" style="font-size:0.95rem;padding:15px 36px;">
          Book a discovery call
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="12" height="12" rx="1.5"/><path d="M5 1v4M11 1v4M2 7h12"/></svg>
        </a>
```

- [ ] **Step 3: Verify**

Read back lines 1735–1746 of `index.html` and confirm:
1. Description ends with "Book a free 30-minute discovery call — I'll map out exactly how to fix it."
2. Button `href` is `https://calendar.app.google/mqn9R7rEz5u25Q8r8`
3. Button has `target="_blank"` and `rel="noopener noreferrer"`
4. Button text is "Book a discovery call"
5. Button icon is the calendar SVG (rect + path), not the arrow
6. "View my work" ghost button directly after is unchanged
