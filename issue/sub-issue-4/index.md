# EPIC 4: The Mailbox Engine (Classic vs Modern)

**Priority:** 🟠 P1 - High (Core UX Feature)
**Dependencies:** EPIC 1 & 2 (Infrastructure & Auth), EPIC 3 (Mail Categories for filtering)
**Execution Order:** Can be parallel with EPIC 3, or after

This epic covers the implementation of switchable mailbox layouts with folder navigation.

## Sub-Issues

1. **[Issue #4.1: Layout Switcher & Preference Sync](./4.1-layout-switcher-preference-sync.md)** — 🟠 **P1**
   - Build layout toggle system and persist preference in Appwrite user profile

2. **[Issue #4.2: Classic View Implementation (Master-Detail)](./4.2-classic-view-master-detail.md)** — 🟡 **P2**
   - Build traditional "e-Office" style layout with resizable panels and compact table

3. **[Issue #4.3: Modern View Implementation (Gmail-style)](./4.3-modern-view-gmail-style.md)** — 🟡 **P2**
   - Build clean, minimalist inbox view with single column list and full-page reading mode

4. **[Issue #4.4: Dynamic Folder Sidebar (Tree View)](./4.4-dynamic-folder-sidebar.md)** — 🟡 **P2**
   - Display dynamic folder structure from API with tree navigation and unread count badges

## Recommended Execution Order
```
4.1 → (4.2 → 4.3 can be parallel) → 4.4
```

## Priority Matrix

| Issue | Priority | Reason |
|-------|----------|--------|
| 4.1 | P1 | Layout switching foundation |
| 4.2 | P2 | Core feature, can be parallel with 4.3 |
| 4.3 | P2 | Core feature, can be parallel with 4.2 |
| 4.4 | P2 | Needed for navigation, depends on API |

## Technical Notes

- **Always use `/api/mail-service`** — never direct backend IP
- **60:30:10 color rule** — 60% `bg-slate-50` (content), 30% `bg-indigo-900` (sidebar), 10% `bg-amber-500` (actions)
- **No `any` types** — use proper interfaces from OpenAPI specs
- **Feature-based structure** — co-locate in `src/features/mailbox/`
- Layout preference stored via Appwrite `account.updatePrefs()`
- Classic view uses `ResizablePanel` from Radix/ShadcnUI
- Modern view uses single-column list with full-page reading mode