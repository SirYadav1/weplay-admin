# WePlay Admin Panel

Standalone single-file admin UI for the WePlay clone backend. Vanilla
HTML/CSS/JS — zero framework, ~15 KB, instant load, industry-standard
sidebar + table layout.

## Run

The backend serves it directly at `/admin-panel/` once the server is
running. Or serve standalone:
```bash
python3 -m http.server 8093
```

## Login

First registered backend user (uid 1) is auto-promoted to admin on signup
(`MaybePromoteFirstAdmin`). Set the backend URL on the login form.

## Features (all live against /admin/*)
| Tab | Actions |
|---|---|
| Dashboard | live counters, mini audit feed |
| Users | search, promote/demote, coin adjust (modal, audited), VIP tier set, ban/unban (sessions revoked) |
| Rooms | list, delete |
| Reports | user reports + bug reports merged, resolve |
| Audit | full admin action log |

## Security
- All /admin/* endpoints gated server-side (Bearer + users.is_admin=1)
- Self-demotion blocked server-side
- Every mutating action audited into admin_audit (visible in panel)
- Ban revokes all sessions immediately
- No secrets embedded — backend URL is user-supplied per login
