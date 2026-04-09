# Button Pulse Glow Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a breathing red glow animation to all `.btn-primary` buttons so they draw the eye at idle, while keeping `.btn-ghost` calm and secondary.

**Architecture:** Pure CSS change inside the existing `<style>` block in `index.html`. Add a `@keyframes pulseGlow` definition, apply it to `.btn-primary`, update the hover state to cancel it, and wrap the animation in a `prefers-reduced-motion` media query for accessibility.

**Tech Stack:** Vanilla CSS (no build step, no dependencies)

---

### Task 1: Add `@keyframes pulseGlow` and apply to `.btn-primary`

**Files:**
- Modify: `index.html:338-374`

- [ ] **Step 1: Add the `pulseGlow` keyframe and update `.btn-primary`**

In `index.html`, locate the `.btn-primary` rule starting at line 338. Replace the entire `.btn-primary` block (lines 338–374, covering the base rule, `::before`, `:hover`, and `:active`) with the following:

```css
    /* ── Buttons ── */
    .btn-primary {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 13px 28px;
      background: var(--accent);
      color: #fff;
      font-weight: 600;
      font-size: 0.875rem;
      border-radius: 6px;
      border: 1px solid var(--accent);
      text-decoration: none;
      letter-spacing: 0.01em;
      position: relative;
      overflow: hidden;
      transition: background 0.2s ease, transform 0.2s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.2s ease;
    }
    /* Shimmer sweep */
    .btn-primary::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(105deg, transparent 40%, rgba(255,255,255,0.18) 50%, transparent 60%);
      transform: translateX(-100%);
      transition: transform 0.55s ease;
    }
    .btn-primary:hover::before { transform: translateX(100%); }
    .btn-primary:hover {
      background: #be123c;
      transform: translateY(-3px) scale(1.03);
      box-shadow: 0 12px 40px rgba(225,29,72,0.5), 0 0 0 1px rgba(225,29,72,0.3);
      animation: none;
    }
    .btn-primary:active {
      transform: translateY(0) scale(0.98);
      box-shadow: none;
      transition-duration: 0.08s;
    }

    @media (prefers-reduced-motion: no-preference) {
      .btn-primary {
        animation: pulseGlow 2.4s ease-in-out infinite;
      }
      @keyframes pulseGlow {
        0%, 100% { box-shadow: 0 0 0 0 rgba(225,29,72,0); }
        50%       { box-shadow: 0 0 18px 6px rgba(225,29,72,0.35); }
      }
    }
```

- [ ] **Step 2: Verify in browser**

Open `index.html` in a browser (or refresh if already open via `serve.mjs`). Check:
- All primary buttons ("Let's Talk", "See my work", "Work with me", "Send me a message") pulse a soft red glow at idle.
- Hovering a primary button stops the pulse and shows the lift + shimmer + strong glow.
- Ghost buttons ("Get in touch", "View my work") have no idle animation.
- In a browser with `prefers-reduced-motion: reduce` set (DevTools > Rendering panel), buttons have no pulse animation.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add pulse glow idle animation to primary buttons"
```
