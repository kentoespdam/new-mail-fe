# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Digital correspondence management system (**surat digital**) for PERUMDAMTS. Greenfield project — follow the epic roadmap in `issue/0-blueprint/`.

## Tech Stack

- **Framework:** Next.js 16.2.2 (App Router, TypeScript)
- **Auth:** Appwrite REST v1.3.x — session mirroring to HttpOnly cookies, server-side JWT caching
- **Data:** TanStack Query v5, TanStack Table v8 (server-side pagination)
- **Forms:** React Hook Form + Zod (schemas derived from OpenAPI 3.1.0)
- **UI:** Tailwind CSS + ShadcnUI

## Architecture

```
src/
├── app/              # App Router pages, layout.tsx, globals.css
├── features/         # Feature modules (mail, admin, auth) — smart components & hooks
├── components/ui/    # ShadcnUI primitives (dumb components)
├── services/         # API clients → /api/mail-service/*
├── lib/              # appwrite-rest.ts, jwt-cache.ts
├── hooks/            # Shared custom hooks
└── validations/      # Zod schemas (OpenAPI 3.1.0 based)
```

### Proxy Engine (`proxy.ts` at project root)

All backend calls go through `/api/mail-service/*` → proxy validates HttpOnly session cookie → fetches cached JWT via `getValidJWT()` → injects `Authorization: Bearer <JWT>` → rewrites to `http://192.168.1.214:8081/api/v1`. Enforces RBAC via Appwrite `labels[]`.

## Critical Rules

1. **No direct backend IP** — never call `192.168.1.214` from client code. Always use `/api/mail-service/*`.
2. **No `any`** — use typed interfaces for all API contracts.
3. **Feature-based structure** — co-locate smart components, hooks, and logic in `src/features/[module]/`.
4. **401 handling** — clear cookies + redirect to `/login`.
5. **Auto-save drafts** — 2-3s debounce via TanStack Mutation.

## Design System (60:30:10)

| Role | Color | Usage |
|------|-------|-------|
| 60% Base | `bg-slate-50` | Content areas, tables |
| 30% Secondary | `bg-indigo-900` | Sidebar, nav, headers |
| 10% Accent | `bg-amber-500` | CTAs, primary buttons, status indicators |

Register these in `tailwind.config.ts`. Two switchable layouts: **Classic** (Master-Detail) and **Modern** (Gmail-style).

## RBAC

- `admin` label → master data endpoints (`/mail-types`, `/mail-categories`, `/file-rules`)
- `staff` label → mail operations (`/mails`, `/mail/folders`)

## API Endpoints (via proxy)

- `/api/v1/mails` — CRUD, Draft, Send, Thread, Search
- `/api/v1/mail/folders` — folder tree
- `/api/v1/mail/types`, `/categories`, `/file-rules` — master data
- `/api/v1/archives` — archived mail

## Epic Roadmap

Detailed plans in `issue/0-blueprint/`:
1. Init & Infra
2. Security Gate (session mirroring, JWT, RBAC)
3. Admin Master Data CRUD
4. Mailbox Engine (switchable layouts)
5. Smart Composer (auto-save, batch recipients)
6. Onboarding & Help (tour guide, Help FAB)

## Instructions for Claude Code
always use bun when running scripts (e.g., `bun run dev`, `bun run build`).
always use skill `context7` when working on code in this repository. always use `bun run lint` and `bun run format` before committing code.