# EPIC 5: Smart Composer & Auto-save Logic

**Priority:** 🟡 P2 - Medium (Smart Feature, depends on EPIC 3 & 4)
**Dependencies:** EPIC 3 (Quick Messages, Mail Types), EPIC 4 (Mailbox Layout)
**Execution Order:** After mailbox engine and master data are complete

This epic covers the intelligent mail composition features including auto-save drafts, attachment management, recipient handling, and template integration.

## Sub-Issues

1. **[Issue #5.1: Debounced Auto-save Engine](./5.1-debounced-auto-save-engine.md)** — 🟠 **P1**
   - Implement auto-save with 2-3 second debounce using TanStack mutations
   - Display save status indicators (Saving, Saved, Failed)
   - Handle draft ID lifecycle (POST for new, PUT for existing)

2. **[Issue #5.2: Attachment Management (File Rules Integration)](./5.2-attachment-management.md)** — 🟡 **P2**
   - Fetch and validate files against File Rules from Master Data
   - Client-side validation with Zod (file extension, max size)
   - Upload with progress bar for large files

3. **[Issue #5.3: Recipient & Template Integration](./5.3-recipient-template-integration.md)** — 🟡 **P2**
   - Multi-select/Tag input for recipients
   - Quick messages dropdown integration
   - Auto-populate editor with template content

## Recommended Execution Order
```
5.1 → 5.3 → 5.2
```

## Priority Matrix

| Issue | Priority | Reason |
|-------|----------|--------|
| 5.1 | P1 | Core feature, auto-save is critical UX |
| 5.2 | P2 | Depends on 3.6 (File Rules), can be later |
| 5.3 | P2 | Depends on 3.7 (Quick Messages) |

## Technical Notes

- **React Hook Form + Zod**: Handle complex form state with proper validation schemas
- **Debounce Strategy**: Use `lodash.debounce` or custom hook for auto-save logic
- **File Upload**: `multipart/form-data` via proxy with progress tracking
- **Color Usage**: 10% Amber-500 only for primary actions like "Kirim Surat"
- **Auto-save Timing**: 2-3 seconds after user stops typing

## Acceptance Criteria

- Drafts auto-save to server every 3 seconds after user stops typing
- Files not matching admin rules are rejected before upload
- Quick messages auto-populate email content
- Recipients managed intuitively (email-style tag input)
