# Dark & Silver Theme — Design Spec

**Date:** 2026-04-10
**Status:** Approved

## Goal

Replace all rose/red accent colors in the portfolio with a warm platinum silver palette. Dark background stays. Every instance of the red accent — CSS variables, hardcoded rgba values, hex values, URL-encoded SVG colors, and canvas JS — gets replaced.

## Color Mapping

| Usage | Before | After |
|---|---|---|
| `--accent` CSS variable | `#e11d48` | `#c9b99a` |
| `--accent-glow` CSS variable | `rgba(225, 29, 72, 0.18)` | `rgba(201, 185, 154, 0.18)` |
| Tailwind `rose.500` | `#e11d48` | `#c9b99a` |
| Tailwind `rose.600` | `#be123c` | `#b0a088` |
| `::selection` background | `rgba(225, 29, 72, 0.25)` | `rgba(201, 185, 154, 0.25)` |
| All `rgba(225,29,72,X)` instances | red rgba | `rgba(201,185,154,X)` — opacity preserved |
| Hardcoded `#e11d48` hex | red | `#c9b99a` |
| Hardcoded `#be123c` hex | dark red | `#b0a088` |
| URL-encoded `%23e11d48` in SVG | `%23e11d48` | `%23c9b99a` |
| Canvas JS `rgba(225,29,72,X)` | red rgba | `rgba(201,185,154,X)` — opacity preserved |

## Scope

Single file: `index.html`

Locations:
- `:root` CSS variables (lines ~47–48)
- Tailwind config in `<script>` block (lines ~29–30)
- `::selection` rule (line ~80)
- Custom cursor CSS (lines ~105, 116, 130)
- Nav/button/tag CSS (lines ~160, 167, 366, 368, 378, 379, etc.)
- About photo ring CSS (lines ~480, 488)
- Various section glow/border/bg rules (~30 instances)
- SVG background pattern inline style (line ~1484)
- Canvas JS drawing code (lines ~1969, 1981, 1995, 1998, 2005, 2350)
- Workflow card JS color values (lines ~2260, 2268)

**Total instances: ~40**

## What Does NOT Change

- Background colors (`--bg`, `--surface`, `--surface-2`, `--border`)
- Text colors (`--text`, `--text-muted`)
- Font, layout, spacing, animations
- Any non-red color values
