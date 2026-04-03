# QWEN.md — Mail Service PERUMDAMTS

Digital correspondence management system (**surat digital**) for PERUMDAMTS. Built with **Next.js 16.2.2** (App Router, TypeScript), connecting to backend `http://192.168.1.214:8081/api/v1` exclusively via root **`proxy.ts` middleware**.

**Tech**: Next.js 16.2.2 · Appwrite v1.3.x REST · TanStack Query v5 & Table v8 · Tailwind CSS + ShadcnUI · React Hook Form + Zod

---

## Architecture

```
src/
├── app/              # App Router (layout.tsx, globals.css)
├── features/         # Feature modules (mail, admin, auth) — smart components/hooks
├── components/ui/    # ShadcnUI primitives
├── services/         # API client → /api/mail-service
├── lib/              # appwrite-rest.ts, jwt-cache.ts
├── hooks/            # Shared custom hooks
└── validations/      # Zod schemas (from OpenAPI 3.1.0)
```

### Proxy Engine (`proxy.ts`) — Core

Intercepts `/api/mail-service/*` → validates HttpOnly session cookie → gets cached JWT via `getValidJWT()` → injects `Authorization: Bearer <JWT>` → rewrites to backend. Enforces RBAC via Appwrite `labels[]` (`admin` for master data, `staff` for mail/folders).

### Security

- **Session mirroring**: Appwrite TTL → HttpOnly cookies (`httpOnly: true, secure: true, sameSite: 'lax'`)
- **JWT caching**: Server-side in-memory cache to prevent 429 rate limits
- **RBAC**: `admin` → `/mail-types`, `/mail-categories`, `/file-rules`; `staff` → `/mails`, `/mail/folders`
- **No direct IP**: All backend calls via `/api/mail-service/` only

---

## Design System (60:30:10)

| 60% Base | 30% Secondary | 10% Accent |
|---|---|---|
| `bg-slate-50` — content, tables | `bg-indigo-900` — sidebar, nav, headers | `bg-amber-500` — CTAs, buttons, status |

Register in `tailwind.config.ts`. Apply to every component.

---

## Conventions

- **No `any`** — use interfaces from OpenAPI specs
- **Feature-based** structure — co-locate related code in `src/features/[module]/`
- **Forms**: RHF + Zod, auto-save drafts with 2-3s debounce via TanStack mutations
- **Error handling**: Proxy-level `try-catch`; 401 → clear cookie + redirect to login
- **Smart components** in features, **dumb components** in `src/components/`

---

## API Endpoints

`/api/v1/mails` (CRUD, Draft, Send, Thread, Search) · `/api/v1/mail/folders` (tree) · `/api/v1/mail/types` · `/api/v1/mail/categories` · `/api/v1/mail/file-rules` · `/api/v1/archives`

---

## Roadmap (Epics)

1. **Init & Infra** — Next.js, Tailwind 60:30:10, TanStack, Appwrite REST, `proxy.ts`
2. **Security Gate** — Session mirroring, JWT lifecycle, RBAC, error/timeout handling
3. **Admin Master Data** — CRUD mail types, categories, file rules
4. **Mailbox Engine** — Switchable Classic/Modern layouts, folder tree
5. **Smart Composer** — Auto-save drafts, discard confirm, batch recipients, quick messages
6. **Onboarding & Help** — Tour guide (Joyride/Shepherd), Help FAB

---

## Code Generation Rules

1. **Always `/api/mail-service`** — never raw backend IP
2. **No `any`** — proper interfaces only
3. **60:30:10 color rule** — strict adherence in every component
4. **Feature-based structure** — co-locate in `src/features/[module]/`
5. **Zod + TanStack** — all forms and data fetching
6. **Use `context7-mcp` skill** — best practices for Next.js, Appwrite REST, TanStack, Tailwind
