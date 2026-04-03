## Issue #5: Auto-save Drafts & Mail Composition Logic

**Priority:** 🟡 P2 - Medium (Smart Feature, depends on EPIC 3 & 4)
**Dependencies:** #3 (Quick Messages, Mail Types), #4 (Mailbox Layout)
**Execution Order:** After mailbox engine and master data are complete

**Description:**
Membangun editor surat pintar dengan fitur simpan otomatis dan manajemen penerima.

**Tasks:**
- [ ] Setup `useForm` with Zod for `MailCreateRequest`.
- [ ] Implement **Debounced Auto-save**:
  - Trigger `POST /api/v1/mails` for first save.
  - Trigger `PUT /api/v1/mails/{id}` for subsequent edits.
- [ ] Add **Discard** button with Alert Confirmation to trigger `DELETE /api/v1/mails/{id}`.
- [ ] Integrate **Quick Messages** dropdown to populate mail content.
- [ ] Implement **Batch Recipient** management.

**Acceptance Criteria:**
- Drafts are saved automatically 2-3 seconds after typing stops.
- Status indicator shows "Saving..." or "Last saved at HH:mm".
