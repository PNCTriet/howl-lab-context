# Brief DEVIN — T14 API keys (để relaunch)

> Nguồn: tin nhắn đầu tiên (prompt) của cloud agent run `bc-48727517-c361-57a7-9734-84b2c1666e7b`, lưu tại `/workspace/cloud-agent-transcripts/bc-48727517-c361-57a7-9734-84b2c1666e7b.jsonl` trên box. Run chạy 2026-09-29 ~02:42–02:44 (giờ VN) rồi bị huỷ; không có branch/PR. Nội dung dưới đây giữ nguyên văn (tiếng Anh) để dán lại khi relaunch.

> Lưu ý khi relaunch: theo ADR-016 key là `pk_live_`/`pk_test_` + 32 random bytes, sha256, hết hạn mặc định 90 ngày; T14 phụ thuộc T07/T11/T12 trong phase-1-plan.md. Commit phải author là PNCTriet (xem 03-personal-os.md).

---

Budget is tight: do only T14, read only the docs and code you need, and finish in one run.

Task: implement T14 API keys for Personal OS (Next.js 16 App Router + TS strict + Supabase). Spec: the T14 section of docs/phase-1-plan.md, ADR-002 in docs/decisions.md, and the API-key parts of docs/security.md and docs/api.md. Follow the existing module and repository patterns (ADR-001 boundaries; each module has a demo in-memory repo and a Supabase repo).

Requirements:
- Keys look like `pk_...`. Store only a hash plus a short display prefix; return the plaintext exactly once at creation.
- Keys are named (one per bot), carry scopes per ADR-002, and support revocation and last_used_at.
- /api/v1 accepts either the owner session or `Authorization: Bearer pk_...`. Revoked or invalid keys get 401, missing scope gets 403.
- Endpoints to create, list and revoke keys, restricted to the owner session.
- Works in demo mode and Supabase mode. Put the SQL in a NEW migration under supabase/migrations with RLS; don't edit existing migrations.
- Minimum tests: hashing and verify, auth resolution (session, valid key, revoked key, wrong scope). Add Vitest only if no test runner exists.

Out of scope: T11 (beyond the minimal scope check T14 needs), T12, T13, the DB types script, and UI files.
The repo is public, so never commit secrets and use obviously fake keys in tests.
Don't touch .github/workflows. No Supabase project exists yet (known blocker).

Done when: typecheck, lint, build and tests pass, and a PR from branch feat/core-api is open against main (do NOT merge). The PR summary covers the key lifecycle, the migration, test results and known gaps. Update docs/api.md briefly.
