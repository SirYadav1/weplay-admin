# WePlay Admin

Standalone admin panel for the WePlay clone backend (`Weplay-open/server`).
Talks to the `/admin/*` API only — no backend code lives here.

## Run
Any static server:
```bash
python3 -m http.server 8092
```
Open http://localhost:8092 — set the backend URL in the login form
(default backend: http://107.148.225.79:8080).

## Login
First registered backend user (uid 1) is auto-promoted to admin.

## Features
- Dashboard counters (users/rooms/messages/gifts)
- Users: search, promote/demote, coin adjust (audited), ban/unban
- Rooms: list, delete
- Reports: list, resolve

## API contract
See Weplay-open/server/CONTRACT.md — Admin panel section.
