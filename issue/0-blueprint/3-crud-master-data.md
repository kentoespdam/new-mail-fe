## Issue #3: CRUD Master Data Dashboard for Admin

**Priority:** 🟠 P1 - High (Prerequisite for Mail Features)
**Dependencies:** #1, #2 (Proxy & Auth working)
**Execution Order:** After authentication gate is complete

**Description:**
Membangun modul manajemen data master yang merupakan prasyarat utama fungsi persuratan.

**Tasks:**
- [ ] Create Zod schemas for `mail-types`, `mail-categories`, and `file-rules`.
- [ ] Build reusable `<AdminDataTable />` using TanStack Table.
- [ ] Implement CRUD for **Mail Types**: `GET /api/v1/mail-types`, `POST`, `PUT`, `DELETE`.
- [ ] Implement CRUD for **Mail Categories**: `GET /api/v1/mail-categories` with `mailTypeId` dropdown.
- [ ] Implement **File Rules** UI for managing allowed extensions and max size.

**Acceptance Criteria:**
- Admin can create, edit, and delete all master data.
- Validation errors are displayed correctly via ShadcnUI Form.
