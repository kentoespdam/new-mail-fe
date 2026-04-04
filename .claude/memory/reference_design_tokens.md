---
name: Design token reference
description: 60:30:10 OKLCH color values used in globals.css — look here when theming
type: reference
---

Configured in `src/app/globals.css` via CSS variables + `@theme` (Tailwind v4).

| Role | Light | Dark |
|------|-------|------|
| 60% Base (bg) | slate-50 `oklch(0.984 0.003 247.858)` | `oklch(0.205 0.042 265.755)` |
| 30% Secondary (primary/sidebar) | indigo-900 `oklch(0.272 0.162 267.133)` | indigo-300 `oklch(0.685 0.169 263.69)` |
| 10% Accent (accent/ring) | amber-500 `oklch(0.821 0.171 83.612)` | amber-400 `oklch(0.852 0.158 84.429)` |

15 ShadcnUI components in `src/components/ui/`: badge, button, card, dialog, dropdown-menu, input, label, select, separator, sheet, sonner, table, tabs, textarea, tooltip.
