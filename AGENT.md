# 🤖 AGENT.md: Mail Service PERUMDAMTS

## 📌 Context & Architecture
Digital correspondence system using **Next.js 16.2.2 (App Router)**.
- **Proxy Gateway:** All backend calls MUST use `/api/mail-service/*` (proxied to `http://192.168.1.214:8081/api/v1`).
- **Auth Flow:** Appwrite REST v1.3.x → Mirror Session to HttpOnly Cookies → Server-side JWT Caching → Inject `Authorization: Bearer <JWT>` in `proxy.ts`.
- **RBAC:** Check Appwrite `labels[]` (admin/staff) in proxy & UI.

## 🛠 Tech Stack (Strict)
- **Data:** TanStack Query v5 & Table v8 (Server-side pagination).
- **Forms:** React Hook Form + Zod (Strict validation).
- **UI:** Tailwind CSS + ShadcnUI.
- **Spec:** OpenAPI 3.1.0 (No `any`, use generated interfaces).

## 🎨 Design System (60:30:10 Rule)
- **60% Base:** `bg-slate-50` (Content/Tables).
- **30% Secondary:** `bg-indigo-900` (Sidebar/Nav/Header).
- **10% Accent:** `bg-amber-500` (CTA/Primary Actions/Status).
- **Layouts:** `Classic` (Master-Detail) & `Modern` (Gmail-style).

## 📁 Folder Structure
```text
src/
├── features/[module]/ # Logic, smart components, hooks (Feature-based)
├── services/          # API clients (calling /api/mail-service)
├── lib/               # Infrastructure (appwrite, jwt-cache)
├── validations/       # Zod schemas (OpenAPI 3.1.0 based)
```

## 📜 Coding Rules
1. **Zero Direct IP:** Never call `192.168.1.214` from client. Use proxy.
2. **Type Safety:** `interface` required for all API contracts. `any` is forbidden.
3. **Smart Composer:** Implement 2-3s debounce auto-save for drafts via TanStack Mutation.
4. **Error Handling:** 401 triggers cookie clear + redirect to `/login`.
5. **UI Logic:** Use `src/features` for data-connected components; `src/components/ui` for primitives.

## 📡 Key Endpoints
- `mails`: `/api/v1/mails` (Draft, Send, Thread).
- `meta`: `/api/v1/mail/folders`, `/types`, `/categories`, `/file-rules`.
- `admin`: RBAC protected master data.

---
**Instruction:** Follow Epic roadmap (1-6) and use `context7` for latest TanStack/Next.js best practices. Standby for task execution.