## Issue #4: Switchable Mailbox Layout (Classic vs Modern)

**Priority:** 🟠 P1 - High (Core UX Feature)
**Dependencies:** #1, #2 (Proxy & Auth), #3 (Mail Categories for filtering)
**Execution Order:** Parallel with or after EPIC 3

**Description:**
Implementasi fitur perpindahan tampilan antara "Gmail-style" dan "e-Office Classic" berdasarkan preferensi pengguna di Appwrite.

**Tasks:**
- [ ] Create layout toggle logic using Appwrite `account.updatePrefs()`.
- [ ] **Modern View**: Implement Gmail-like list with snippet and single-page reading.
- [ ] **Classic View**: Implement Master-Detail view with `ResizablePanel`.
  - **Top**: Compact TanStack Table.
  - **Bottom**: Preview Pane for mail content.
- [ ] Build **Tree View** Sidebar for folders using `GET /api/v1/mail/folders`.

**Acceptance Criteria:**
- Users can toggle layouts and the preference is persisted in Appwrite.
- Classic view mimics the provided screenshot layout.
