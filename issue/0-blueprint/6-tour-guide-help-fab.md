## Issue #6: Interactive Tour Guide & Help FAB

**Priority:** 🟢 P3 - Low (UX Enhancement/Polish)
**Dependencies:** #4 (Layout switching must be complete)
**Execution Order:** Last epic, after all core features are working

**Description:**
Meningkatkan kemudahan penggunaan (UX) bagi pengguna baru melalui panduan interaktif.

**Tasks:**
- [ ] Integrate `React Joyride` or `Shepherd.js`.
- [ ] Create adaptive tour steps for both **Classic** and **Modern** layouts.
- [ ] Add **Skip** button on the tour that updates `tour_completed: true` in Appwrite Prefs.
- [ ] Implement Floating Action Button (FAB) with `?` icon (Amber-500) at bottom right.
- [ ] FAB Menu: "Repeat Tour" and "Help Center".

**Acceptance Criteria:**
- Tour automatically starts for first-time users.
- Help button is globally accessible.

---

> **Notes for AI Agent/Junior Dev:**
> "Focus on Type-Safety. Do not use `any`. Always use the Proxy URL `/api/mail-service` for external calls. Follow the 60:30:10 color rule strictly in every component."
