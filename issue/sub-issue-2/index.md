# EPIC 2: Security & Authentication Gate

**Priority:** 🔴 P0 - Critical (Security Gate)
**Dependencies:** EPIC 1 (Infrastructure complete)
**Execution Order:** Immediately after EPIC 1

This epic covers all security and authentication components for the Mail Service application.

## Sub-Issues

1. **[Issue #2.1: Session Mirroring & Server-Side Cookie Management](./2.1-session-mirroring.md)** — 🔴 **P0**
   - Implement HttpOnly cookie-based session management mirroring Appwrite sessions

2. **[Issue #2.2: JWT Lifecycle & Smart Caching Logic](./2.2-jwt-lifecycle.md)** — 🔴 **P0**
   - Build JWT generation and caching utilities to prevent rate limit issues

3. **[Issue #2.3: Root `proxy.ts` - Request Forwarding Engine](./2.3-proxy-forwarding.md)** — 🔴 **P0**
   - Set up proxy to forward requests to PERUMDAMTS external API with JWT injection

4. **[Issue #2.4: Proxy-Level Authorization (RBAC with Labels)](./2.4-rbac-labels.md)** — 🟠 **P1**
   - Implement role-based access control using Appwrite user labels

5. **[Issue #2.5: Global Error & Timeout Handling in Proxy](./2.5-error-handling.md)** — 🟠 **P1**
   - Handle connection failures and session issues gracefully

## Recommended Execution Order
```
2.1 → 2.2 → 2.3 → 2.4 → 2.5
```

## Priority Matrix

| Issue | Priority | Reason |
|-------|----------|--------|
| 2.1 | P0 | Session management foundation |
| 2.2 | P0 | JWT cache required for proxy auth |
| 2.3 | P0 | Blocking all API calls |
| 2.4 | P1 | Can be added after basic auth works |
| 2.5 | P1 | Important but can be iterative |

## Implementation Notes

- Use Appwrite REST API client for full control over request headers
- All backend communication must flow through `/api/mail-service/` only
- Apply 60:30:10 color rule for any UI components (Error, Loading pages)
- Follow Next.js 16.2.2 security standards for session management
