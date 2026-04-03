# EPIC 3: Admin Foundation (Master Data)

**Priority:** 🟠 P1 - High (Prerequisite for Mail Features)
**Dependencies:** EPIC 1 & 2 (Infrastructure & Auth complete)
**Execution Order:** After security gate is complete

This epic covers all admin master data management components for the Mail Service application.

## Sub-Issues

1. **[Issue #3.1: Reusable Admin Data Table & CRUD Layout](./3.1-admin-data-table.md)** — 🟠 **P1**
   - Build reusable table and layout components for all master data modules

2. **[Issue #3.2: Reusable Delete Confirmation Dialog](./3.2-delete-dialog.md)** — 🟠 **P1**
   - Build GitHub-style delete confirmation requiring users to type `HAPUS` to confirm

3. **[Issue #3.3: Reusable Form Input Controls (Shadcn + RHF + Zod)](./3.3-form-inputs.md)** — 🟠 **P1**
   - Build controlled input components integrating ShadcnUI, React Hook Form, and Zod validation

4. **[Issue #3.4: Mail Type Management (CRUD)](./3.4-mail-type-crud.md)** — 🟡 **P2**
   - Implement CRUD for Mail Types (e.g., Internal, External)

5. **[Issue #3.5: Mail Category Management with Type Selection](./3.5-mail-category-crud.md)** — 🟡 **P2**
   - Implement CRUD for Mail Categories linked to Mail Types

6. **[Issue #3.6: File Rules & Allowed Extensions Config](./3.6-file-rules-crud.md)** — 🟡 **P2**
   - Implement file attachment restrictions (extensions, size limits)

7. **[Issue #3.7: Quick Messages & Document Types Management](./3.7-quick-messages-crud.md)** — 🟡 **P2**
   - Implement CRUD for quick message templates and document types

## Recommended Execution Order
```
3.1 → 3.2 → 3.3 → (3.4 → 3.5 → 3.6 → 3.7 can be parallel)
```

## Priority Matrix

| Issue | Priority | Reason |
|-------|----------|--------|
| 3.1 | P1 | Reusable component foundation |
| 3.2 | P1 | Needed for all delete operations |
| 3.3 | P1 | Form inputs needed for all CRUD |
| 3.4 | P2 | First master data module |
| 3.5 | P2 | Depends on 3.4 (needs mail type dropdown) |
| 3.6 | P2 | Required for EPIC 5 (attachments) |
| 3.7 | P2 | Required for EPIC 5 (templates) |

## Technical Notes

- Every `DELETE` action must use `<DeleteConfirmDialog>` from Issue #3.2
- All CRUD forms must use controlled input components from Issue #3.3
- Use `bg-slate-50` (60%) as page background for clean, professional appearance
- Follow **shadcn/ui + React Hook Form + Zod** pattern from official documentation: https://ui.shadcn.com/docs/forms/react-hook-form
- Apply 60:30:10 color rule: 60% `bg-slate-50`, 30% `bg-indigo-900`, 10% `bg-amber-500`
