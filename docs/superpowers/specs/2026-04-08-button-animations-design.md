# Button Animation Design — Pulse Glow

**Date:** 2026-04-08
**Status:** Approved

## Goal

Make the portfolio's CTA buttons more attention-grabbing to potential clients by adding a continuous idle pulse glow animation to the primary button, while keeping the ghost button calm and secondary.

## Approach: Option A — Pulse Glow

Chosen over animated gradient (Option B) and shimmer+border-trace (Option C) because it draws the eye without being distracting, and preserves clear visual hierarchy between primary and secondary buttons.

## Changes

### `.btn-primary` (in `index.html` `<style>` block)

**Add idle pulse animation:**
```css
animation: pulseGlow 2.4s ease-in-out infinite;
```

**Add keyframe definition:**
```css
@keyframes pulseGlow {
  0%, 100% { box-shadow: 0 0 0 0 rgba(225,29,72,0); }
  50%       { box-shadow: 0 0 18px 6px rgba(225,29,72,0.35); }
}
```

**Update hover state** — cancel idle animation and apply enhanced glow:
```css
.btn-primary:hover {
  background: #be123c;
  transform: translateY(-3px) scale(1.03);  /* was 1.02 */
  box-shadow: 0 12px 40px rgba(225,29,72,0.5), 0 0 0 1px rgba(225,29,72,0.3);
  animation: none;
}
```

### `.btn-ghost` — no changes

Ghost button intentionally has no idle animation. Visual hierarchy: primary draws attention, ghost is secondary. Existing hover behaviour (corner brackets, lift, shadow) unchanged.

## Scope

- File: `index.html` only
- No HTML changes, no JavaScript changes
- Affects all 5 button instances:
  - Nav: "Let's Talk"
  - Hero: "See my work" (primary), "Get in touch" (ghost — unchanged)
  - Services: "Work with me"
  - Contact: "Send me a message" (primary), "View my work" (ghost — unchanged)

## Constraints

- Respects `prefers-reduced-motion` — the existing media query on the custom cursor already establishes this pattern; the animation should be wrapped in a `@media (prefers-reduced-motion: no-preference)` block
- No new dependencies, no build step required
