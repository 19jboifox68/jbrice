# About Section — Compact Redesign

**Date:** 2026-04-10
**Status:** Approved

## Goal

Replace the existing full-height About section with a compact, elegant side-by-side layout. Reduce vertical footprint while preserving all content and the existing visual identity (dark theme, rose accent, DM Sans).

## Layout

- **Structure:** Two-column grid (`md:grid-cols-2`), same as current
- **Section padding:** `py-16` (reduced from `py-28`)
- **Column gap:** `gap-12` (reduced from `gap-16`)

## Left Column — Photo

- Photo with rings scaled down ~30%:
  - `about-photo`: ~100px × 100px (from ~180px)
  - `about-photo-ring`: ~110px (inner decorative ring)
  - `about-photo-ring-2`: ~120px (outer decorative ring)
- "Open to Work" badge stays below photo, unchanged
- Column alignment: centered, same as current

## Right Column — Bio

### Label & Heading
- "About me" section label — unchanged
- Heading: "The person behind the automation." — unchanged

### Bio Paragraphs (condensed from 3 → 2)
- **Paragraph 1 (merged):** Combine existing P1 and P2 into one — introduce Brice, mention n8n/Make.com/Zapier/AI agents, and end-to-end pipelines (lead gen, CRM, AI content, knowledge bases).
- **Paragraph 2 (kept as-is):** "With 8+ years in customer service…" line.

### Tool Tags
- All 13 tags kept exactly as-is: n8n, Make.com, OpenAI, Relevance AI, Zapier, Python, Salesforce CRM, GoHighLevel, Airtable, Google Workspace, RAG Systems, AI Agents, Webhooks
- Spacing: `mb-4` (reduced from `mb-8`)

### CTA Button
- "Work with me" → `#contact`, same `.btn-primary` style
- Spacing above: `mb-4` on tags

## Spacing Changes Summary

| Element | Before | After |
|---|---|---|
| Section padding | `py-28` | `py-16` |
| Column gap | `gap-16` | `gap-12` |
| Bio → Tags gap | `mb-8` | `mb-4` |
| Tags → Button gap | `mb-8` | `mb-4` |
| Between bio paragraphs | `space-y-4` | `space-y-3` |

## What Does NOT Change

- Font, colors, accent, dark theme
- Heading text and section label
- All tool tags and their styles
- "Work with me" button style and link target
- Reveal/animation classes
- "Open to Work" badge
- Photo image source
