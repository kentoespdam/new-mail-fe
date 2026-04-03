# 0-Blueprint: Mail Service Development Roadmap

This directory contains the high-level blueprint issues for the Mail Service (PERUMDAMTS) application. Each issue represents a major epic in the development roadmap.

## Blueprint Issues

1. **[Issue #1: Setup Next.js 16.2.2 & Tailwind 60:30:10 Theme](./1-init-nextjs-tailwind.md)**
   - Initialize project with TypeScript, design system, and folder structure

2. **[Issue #2: Implement root `proxy.ts` & Appwrite REST Auth](./2-proxy-appwrite-auth.md)**
   - Build security layer with proxy engine and JWT caching

3. **[Issue #3: CRUD Master Data Dashboard for Admin](./3-crud-master-data.md)**
   - Build master data management module (mail types, categories, file rules)

4. **[Issue #4: Switchable Mailbox Layout (Classic vs Modern)](./4-switchable-mailbox-layout.md)**
   - Implement toggle between Gmail-style and e-Office Classic layouts

5. **[Issue #5: Auto-save Drafts & Mail Composition Logic](./5-auto-save-drafts.md)**
   - Build smart mail editor with debounced auto-save and recipient management

6. **[Issue #6: Interactive Tour Guide & Help FAB](./6-tour-guide-help-fab.md)**
   - Add onboarding tour and floating help button for UX improvement

## Sub-Issues

Detailed sub-issues are organized in separate directories:

- **[EPIC 1: Init & Infrastructure](../sub-issue-1/index.md)**
  - Next.js scaffolding, Tailwind design system, TanStack setup, Appwrite REST, proxy engine

- **[EPIC 2: Security & Authentication Gate](../sub-issue-2/index.md)**
  - Session mirroring, JWT lifecycle, proxy forwarding, RBAC, error handling

- **[EPIC 3: Admin Foundation (Master Data)](../sub-issue-3/index.md)**
  - Reusable components, CRUD for mail types, categories, file rules, quick messages

- **[EPIC 4: Mailbox Engine (Switchable Layout)](../sub-issue-4/index.md)**
  - Layout switcher preference sync, classic view master-detail, modern Gmail-style view, dynamic folder sidebar

- **[EPIC 5: Smart Composer & Auto-save](../sub-issue-5/index.md)**
  - Debounced auto-save engine, attachment management with file rules, recipient & template integration

- **[EPIC 6: User Onboarding & Help](../sub-issue-6/index.md)**
  - Onboarding engine with Appwrite sync, adaptive tour steps, floating help FAB, help center UI, final production polish

## Technical Guidelines

- **Always use `/api/mail-service`** — never direct backend IP
- **No `any` types** — proper interfaces only from OpenAPI specs
- **Feature-based structure** — co-locate in `src/features/[module]/`
- **60:30:10 color rule** — 60% `bg-slate-50`, 30% `bg-indigo-900`, 10% `bg-amber-500`
- **Zod + TanStack** — all forms and data fetching
- **shadcn/ui + RHF** — follow official pattern: https://ui.shadcn.com/docs/forms/react-hook-form
- **Alway use context 7** — for getting bestpractices, performance and latest features
