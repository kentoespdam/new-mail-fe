# EPIC 1: Init & Infrastructure

**Priority:** 🔴 P0 - Critical (Blocking Foundation)
**Dependencies:** None
**Execution Order:** First epic to complete

This epic covers the initial project setup, infrastructure configuration, and foundational architecture for the Mail Service application.

## Timeline Estimasi (6 Bulan / 26 Minggu)

Total estimasi EPIC 1: **~5 minggu**

| Issue | Estimasi | Minggu Mulai | Minggu Selesai |
|-------|----------|--------------|----------------|
| 1.1 Next.js Scaffolding | 1 minggu | Minggu 1 | Minggu 1 |
| 1.2 Tailwind Design System | 1 minggu | Minggu 2 | Minggu 2 |
| 1.3 TanStack Query & Table | 1 minggu | Minggu 5 | Minggu 5 |
| 1.4 Appwrite REST & JWT Cache | 1 minggu | Minggu 3 | Minggu 3 |
| 1.5 Proxy Engine | 1 minggu | Minggu 4 | Minggu 4 |

> **Catatan**: Estimasi ini merupakan bagian dari total proyek 6 bulan (26 minggu). EPIC 1 diharapkan selesai pada **Minggu 1-5**.

## Sub-Issues

1. **[Issue #1.1: Next.js 16.2.2 Scaffolding & Feature-Based Architecture](./1.1-nextjs-scaffolding.md)** — 🔴 **P0** — ⏱️ **1 minggu**
   - Initialize Next.js project with TypeScript and feature-based folder structure

2. **[Issue #1.2: Tailwind Design System (Rule 60:30:10)](./1.2-tailwind-design-system.md)** — 🔴 **P0** — ⏱️ **1 minggu**
   - Configure global design system with PERUMDAMTS color proportions (60:30:10)

3. **[Issue #1.3: TanStack Query & Table Global Setup](./1.3-tanstack-setup.md)** — 🟠 **P1** — ⏱️ **1 minggu**
   - Setup data fetching and table management with TanStack suite

4. **[Issue #1.4: Appwrite REST Client & JWT Cache Utility](./1.4-appwrite-rest-jwt-cache.md)** — 🔴 **P0** — ⏱️ **1 minggu**
   - Build Appwrite REST wrapper and JWT caching system to prevent rate limiting

5. **[Issue #1.5: Core `proxy.ts` Rewrite Engine Implementation](./1.5-proxy-engine.md)** — 🔴 **P0** — ⏱️ **1 minggu**
   - Implement root-level proxy for authentication and request rewriting to PERUMDAMTS API

## Recommended Execution Order
```
1.1 → 1.2 → 1.4 → 1.5 → 1.3
```

## Priority Matrix

| Issue | Priority | Reason |
|-------|----------|--------|
| 1.1 | P0 | Foundation scaffolding, must be first |
| 1.2 | P0 | Design system needed for all UI |
| 1.3 | P1 | Can be parallel with 1.4/1.5 |
| 1.4 | P0 | JWT cache required for proxy |
| 1.5 | P0 | Blocking all API-dependent features |

## Technical Notes

- All backend communication flows through `/api/mail-service/` only (no direct backend IP in frontend)
- Use feature-based structure: co-locate related code in `src/features/[module]/`
- No `any` types — use proper interfaces from OpenAPI specs
- Follow 60:30:10 color rule: 60% `bg-slate-50`, 30% `bg-indigo-900`, 10% `bg-amber-500`
