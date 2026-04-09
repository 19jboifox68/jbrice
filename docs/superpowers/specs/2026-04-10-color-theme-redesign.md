# Color Theme Redesign — Soft Silver Accent

**Date:** 2026-04-10
**Status:** Approved

## Problem

The existing accent color (`#c9b99a`, sandy gold/beige) feels visually off and uncomfortable to look at against the near-black background.

## Goal

Replace every instance of the sandy gold accent with a soft silver (`#d4d4d4`) for a clean, minimal, monochrome aesthetic.

## Changes

All changes are confined to `index.html` CSS (`:root` variables and inline color values).

| Location | Before | After |
|---|---|---|
| `--accent` CSS variable | `#c9b99a` | `#d4d4d4` |
| `--accent-glow` CSS variable | `rgba(201, 185, 154, 0.18)` | `rgba(212, 212, 212, 0.18)` |
| Badge text color (`.badge-available`) | `#ddd0b8` | `#c8c8c8` |
| Inline `rgba(201,185,154,…)` glow values (cursor, hero, ring) | sandy tint | silver equivalent (scale 201→212, 185→212, 154→212) |
| `rgba(201, 185, 154, 0.25)` selection bg | sandy | `rgba(212, 212, 212, 0.25)` |

## What stays the same

- Background (`#060606`), surface, border, text colors — untouched
- All layout, spacing, animations, interactions
- Cursor behavior, badge logic, scroll animations

## Success criteria

- No sandy/warm tones visible anywhere on the page
- Cursor, badge dot, button, hero glow, and selection highlight all render in silver/white
- Site feels clean and monochrome
