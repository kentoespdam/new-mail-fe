## Issue #2: Implement root `proxy.ts` & Appwrite REST Auth

**Priority:** 🔴 P0 - Critical (Security Gate)
**Dependencies:** #1 (Next.js setup)
**Execution Order:** After #1, before any API-dependent features

**Description:**
Membangun sistem keamanan menggunakan `proxy.ts` (standard Next.js 16.2.2) sebagai jembatan ke API eksternal dan integrasi Appwrite REST.

**Tasks:**
- [ ] Create `proxy.ts` at root to handle rewrites for `/api/mail-service/*` to `http://192.168.1.214:8081/api/v1`.
- [ ] Implement Appwrite REST Client in `src/lib/appwrite-rest.ts`.
- [ ] Create `src/lib/jwt-cache.ts` to manage **Appwrite JWT** with caching logic to avoid 429 Rate Limit.
- [ ] Inject JWT into Proxy headers: `Authorization: Bearer <JWT>`.
- [ ] Mirror Appwrite session TTL to Next.js HTTP-only cookies.

**Acceptance Criteria:**
- JWT is successfully injected into proxied requests.
- Rate limiting is mitigated via server-side caching.
