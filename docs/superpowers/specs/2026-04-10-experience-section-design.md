# Experience Section Design

**Date:** 2026-04-10
**Status:** Approved

## Goal

Add a dedicated "Experience" section to the portfolio site, placed between the existing `#about` and `#services` sections, displaying professional history from the resume as a vertical timeline.

## Placement

Insert new `<section id="experience">` immediately after the closing `</section>` tag of `#about` (line ~1377) and before the opening of `#services`.

## Section Header

- Section label: `"Experience"` (uses existing `.section-label` class)
- Heading line 1: `"The work that"`
- Heading line 2: `"built the expertise."` — wrapped in `<span class="text-accent">`
- Uses existing `.section-heading.split-heading` classes

## Timeline Layout

- Left-aligned vertical line: `2px` wide, `rgba(212,212,212,0.15)` color, positioned absolutely on the left side of the content column
- Each entry has:
  - A silver dot (`8px` circle, `background: var(--accent)`) on the timeline line, vertically centered with the role title
  - **Role title** — white, `font-weight: 600`
  - **Company + Date range** — on the same line using `display: flex; justify-content: space-between`. Company in silver accent (`var(--accent)`), dates in muted text (`var(--text-muted)`), both `font-weight: 400`, `font-size: 0.875rem`
  - **Bullet points** — muted text, `font-weight: 300`, `line-height: 1.75`, indented under the header

- Entries ordered newest first
- Each entry wrapped in `.reveal` with staggered delays

## Content — 4 Entries

### Entry 1
- **Role:** AI Automation Specialist (Freelance)
- **Company:** Self-Employed
- **Dates:** Jan 2026 – Present
- **Bullets:**
  - Design and deploy multi-step automation workflows across n8n, Make.com, and Zapier for clients in sales ops, content, and customer support
  - Build webhook-triggered pipelines integrating CRMs, Google Workspace, Slack, and AI APIs (OpenAI, OpenRouter, Gemini)
  - Implement JavaScript code nodes for data transformation, error handling, and conditional routing logic
  - Built and deployed 10+ automation workflows as portfolio projects spanning sales ops, content pipelines, and customer support use cases

### Entry 2
- **Role:** Senior Project Expert
- **Company:** Cognizant
- **Dates:** Jul 2020 – Jan 2026
- **Bullets:**
  - Managed complex client account operations; identified repetitive manual workflows and built internal process documentation to support future automation
  - Gained deep exposure to CRM workflows, ticket routing logic, and SLA-driven escalation patterns — directly informing current automation design work

### Entry 3
- **Role:** Engagement Specialist
- **Company:** Synchrony Financial
- **Dates:** Apr 2019 – Oct 2019
- **Bullets:**
  - Handled billing inquiries and account issue resolution; recognized patterns in manual back-office processes ripe for automation

### Entry 4
- **Role:** Earlier Roles
- **Company:** Contact Solutions · Collabera · Wipro
- **Dates:** Oct 2015 – Feb 2019
- **Bullets:**
  - Customer service and lead generation across inbound and outbound programs; built strong communication and process documentation skills

## CSS

Add minimal new styles inside the existing `<style>` block:

```css
/* ── Experience Timeline ── */
.timeline {
  position: relative;
  padding-left: 32px;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 8px;
  bottom: 0;
  width: 2px;
  background: rgba(212,212,212,0.15);
}
.timeline-entry {
  position: relative;
  padding-bottom: 40px;
}
.timeline-entry:last-child {
  padding-bottom: 0;
}
.timeline-dot {
  position: absolute;
  left: -37px;
  top: 6px;
  width: 10px;
  height: 10px;
  background: var(--accent);
  border-radius: 50%;
  box-shadow: 0 0 8px rgba(212,212,212,0.4);
}
```

## Animations

Each `.timeline-entry` wrapped in `.reveal` with incremental `reveal-delay-N` classes (delay-1 through delay-4).

## Success Criteria

- Section appears between About and Services when scrolling
- Timeline line and dots render correctly in silver
- All 4 entries display with correct role, company, dates, and bullets
- Scroll-reveal animations trigger as user scrolls into the section
- Visually consistent with the rest of the site (spacing, typography, color)
