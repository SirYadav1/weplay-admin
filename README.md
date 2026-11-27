# WePlay Admin Panel

Standalone single-file admin UI for the WePlay clone backend. Vanilla
HTML/CSS/JS — zero framework, no build step, instant load. Professional
neutral slate theme with drawn SVG icons (no emoji, no glow, no neon).

## Run

The backend serves it directly at `/admin-panel/` once the server is
running. Or serve standalone:
```bash
python3 -m http.server 8093
```

## Login

First registered backend user (uid 1) is auto-promoted to admin on signup
(`MaybePromoteFirstAdmin`). Set the backend URL on the login form.
The session token is kept in `sessionStorage`, the backend URL in
`localStorage`; no credentials are stored.

## Features (all live against the backend API)

| Tab | Actions |
|---|---|
| Dashboard | live counters, recent administrator activity |
| Users | server-side search/paging, sorting, promote/demote, coin adjust (modal, audited), VIP tier set, ban/unban with reason (sessions revoked), flower balance column |
| Rooms | list with local paging, delete with confirmation dialog |
| Reports | user reports + bug reports, status/kind filters, local paging, resolve |
| Gift animations | list configured in-house animations, add/edit via modal (`anim_type`, animation/preview/combo/broadcast URLs), backend catalog picker, instant effect on clients |
| Audit | full admin action log with local paging |

Every list view has loading, empty and error states with retry. Destructive
actions use in-app confirmation dialogs instead of native `confirm()`.

## Security
- All `/admin/*` endpoints gated server-side (Bearer + `users.is_admin=1`)
- Self-demotion blocked server-side
- Every mutating action audited into `admin_audit` (visible in the panel)
- Ban revokes all sessions immediately
- No secrets embedded — backend URL is user-supplied per login
