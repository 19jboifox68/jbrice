# Discovery Call CTA Design

**Date:** 2026-04-08
**Status:** Approved

## Goal

Replace the "Send me a message" mailto button in the contact section with a Google Calendar booking link for a discovery call, and update the surrounding copy to match the new intent.

## Changes

### `index.html` — Contact section (lines 1735–1745)

**Description paragraph** — update last sentence:

Current:
> "Have a process you want to automate? A workflow that's costing your team hours every week? Let's talk — I'll build the system that fixes it."

New:
> "Have a process you want to automate? A workflow that's costing your team hours every week? Book a free 30-minute discovery call — I'll map out exactly how to fix it."

**Primary button** — replace the mailto anchor:

Current:
```html
<a href="mailto:hello@brice.dev" class="btn-primary" style="font-size:0.95rem;padding:15px 36px;">
  Send me a message
  <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8h12M9 3l5 5-5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
</a>
```

New:
```html
<a href="https://calendar.app.google/mqn9R7rEz5u25Q8r8" target="_blank" rel="noopener noreferrer" class="btn-primary" style="font-size:0.95rem;padding:15px 36px;">
  Book a discovery call
  <svg width="16" height="16" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="12" height="12" rx="1.5"/><path d="M5 1v4M11 1v4M2 7h12"/></svg>
</a>
```

## Unchanged

- Ghost button: "View my work" (href="#work") — untouched
- Social links row — untouched
- Section heading: "Let's build your automation." — untouched
- Section label: "Let's build together" — untouched
- Nav "Let's Talk" button — links to `#contact`, stays as-is
- Hero "Get in touch" ghost button — stays as-is

## Scope

- File: `index.html` only
- No CSS changes, no JavaScript changes
- Two edits: description text + primary button anchor
