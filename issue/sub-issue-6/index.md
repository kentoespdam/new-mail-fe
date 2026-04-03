# EPIC 6: User Onboarding & Help

**Priority:** 🟢 P3 - Low (UX Enhancement/Polish)
**Dependencies:** EPIC 4 (Layout switching must be complete)
**Execution Order:** Last epic, after all core features are working

This epic covers the user onboarding, tour guide, help center, and final production polish to ensure a smooth user experience for PERUMDAMTS staff.

## Sub-Issues

1. **[Issue #6.1: Onboarding Engine & Appwrite Sync](./6.1-onboarding-engine-appwrite-sync.md)** — 🟢 **P3**
   - Install react-joyride or shepherd.js
   - Build `useOnboarding` hook with Appwrite `account.getPrefs()` integration
   - Implement Skip button with `PATCH /account/prefs` sync
   - Tour triggers only on first login at `/inbox`

2. **[Issue #6.2: Adaptive Tour Steps (Layout Aware)](./6.2-adaptive-tour-steps.md)** — 🟢 **P3**
   - Configure tour steps for Classic template (sidebar, toolbar, table, preview)
   - Configure tour steps for Modern template (FAB, inbox list, search)
   - Use 10% Amber-500 for "Lanjut" buttons in tour dialogs
   - Steps adapt based on active layout preference

3. **[Issue #6.3: Floating Help Action Button (FAB)](./6.3-floating-help-fab.md)** — 🟢 **P3**
   - Build `HelpFAB` component with fixed positioning (bottom-right)
   - Amber-500 background for visibility
   - Popover menu: "Ulangi Panduan", "Hubungi IT Support", "Pusat Bantuan"
   - Works across all dashboard pages

4. **[Issue #6.4: Documentation & Help Center UI](./6.4-help-center-ui.md)** — 🟢 **P3**
   - Build `HelpCenter` modal with ShadcnUI Dialog
   - Organize help content by category (Admin, Writing Mail, Managing Folders)
   - Use visual elements (images/icons) for clarity
   - Responsive and readable modal design

5. **[Issue #6.5: Final Polish & Production Ready](./6.5-final-polish-production.md)** — 🟡 **P2**
   - Remove all `console.log` and enable proxy compression
   - Install loading skeletons across all modules
   - Verify JWT caching for 429 rate limit prevention
   - Final 60:30:10 color rule audit across all pages

## Recommended Execution Order
```
6.5 (start early) → 6.1 → 6.2 → 6.3 → 6.4
```

## Priority Matrix

| Issue | Priority | Reason |
|-------|----------|--------|
| 6.1 | P3 | Enhancement, not blocking |
| 6.2 | P3 | Depends on 6.1 and layout switching |
| 6.3 | P3 | Nice-to-have, can be last |
| 6.4 | P3 | Documentation, can be iterative |
| 6.5 | P2 | Should start before production deploy |

## Technical Notes

- **Tour Library**: `react-joyride` (recommended) or `shepherd.js`
- **Appwrite Integration**: `account.updatePrefs()` for `tour_completed` flag
- **Color Usage**: 10% Amber-500 for FAB and tour "Lanjut" buttons
- **Help FAB**: Fixed position, appears on all dashboard pages
- **Skip Logic**: `PATCH /account/prefs` → `{ tour_completed: true }`

## Acceptance Criteria

- Tour auto-runs on first login, skips permanently when user presses "Skip"
- Tour steps point to correct elements regardless of active layout
- Help FAB is accessible on all dashboard pages
- Help Center modal is responsive and self-service
- Production build is clean (no debug code), performant, and visually consistent
