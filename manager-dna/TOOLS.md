# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

<!-- FORGE:STANDARD:google-workspace v1.0 -->
## Google Workspace (Standard)

If your agent has Google Workspace connected:
- Use `GOG_ACCOUNT=<your-email>@venturehome.com` for all gog commands
- Available services: Gmail, Calendar, Drive, Contacts, Docs, Sheets
- Always use your assigned VH email — never use personal accounts for company work
- Calendar invites should include a clear agenda in the description
- Email signatures should include your name and "Venture Home" affiliation
<!-- /FORGE:STANDARD:google-workspace -->

<!-- FORGE:STANDARD:forge-api v1.0 -->
## Forge API Access

- **Base URL:** `https://forge.venturehome.com`
- **Auth:** POST `/api/auth/login` with `{ email, password }` → returns Bearer token
- **All API calls** require `Authorization: Bearer <token>` header
- **Content-Type:** `application/json` for all requests
- **Your agent ID and credentials** are in your SOUL.md or IDENTITY.md
- **Heartbeat:** POST `/api/v1/agents/<your-id>/heartbeat` every 30 minutes
- **Rate limiting:** Be reasonable — batch operations where possible, don't poll in tight loops
<!-- /FORGE:STANDARD:forge-api -->

---

## My Setup

### Google Workspace

- Account: rex@venturehome.com
- Services: Gmail, Calendar, Drive, Contacts, Docs, Sheets
- Connected: 2026-02-14 (re-authed from rex.merding@venturehome.com)
- Use `GOG_ACCOUNT=rex@venturehome.com` for all gog commands
- Old account (rex.merding@venturehome.com) still in auth list — can remove when ready

### iMessage

- Alex's number: +12038583051
- Chat ID: 1
- Tom O'Hearen's number: +19083283208
- Working as of 2026-02-07

### Helix Protocol (DNA Sync)

Bidirectional DNA sync between this machine and Forge. Full architecture → `forge-skills/dna-authoring/SKILL.md`

- **Upstream** (every heartbeat): `forge-sync.sh heartbeat` — sends hashes, uploads changed DNA files
- **Downstream** (daily 3AM): `forge-sync.sh sync` — applies queued MANAGED block updates from Forge
- **Emergency**: Admin pushes from Forge UI → applied on next heartbeat (bypasses daily window)
- **Pending queue**: `~/.forge-sync/pending-templates.json`
- **Env vars**: `FORGE_EMAIL`, `FORGE_PASSWORD`, `AGENT_ID`, `WORKSPACE`, `SKILLS_DIR`, `FORGE_SYNC_TIME`
- **Script location**: `forge-skills/forge-sync/forge-sync.sh` (also `forge/backend/src/assets/forge-sync.sh`)

---

Add whatever helps you do your job. This is your cheat sheet.

<!-- antfarm:workflows -->
# Antfarm Workflows

Antfarm CLI (always use full path to avoid PATH issues):
`node ~/.openclaw/workspace/antfarm/dist/cli/cli.js`

Commands:
- Install: `node ~/.openclaw/workspace/antfarm/dist/cli/cli.js workflow install <name>`
- Run: `node ~/.openclaw/workspace/antfarm/dist/cli/cli.js workflow run <workflow-id> "<task>"`
- Status: `node ~/.openclaw/workspace/antfarm/dist/cli/cli.js workflow status "<task title>"`
- Logs: `node ~/.openclaw/workspace/antfarm/dist/cli/cli.js logs`

Workflows are self-advancing via per-agent cron jobs. No manual orchestration needed.
<!-- /antfarm:workflows -->

<!-- FORGE:STANDARD:forgechat-tools v1.0 -->
## ForgeBot Chat

ForgeBot Chat is Venture Home's internal messaging platform. Use it for agent-to-agent and agent-to-human communication. You are free to message any Forge user — no restrictions. See CONTACTS.md for the full member directory with IDs.

- **API:** POST `/api/v1/chat/conversations/:id/messages` with Bearer token
- **Create DM:** POST `/api/v1/chat/conversations` with `{"participant_ids": ["user-id"]}`
- **Etiquette:** Be concise. Use reactions for quick acks. Don't spam.
<!-- /FORGE:STANDARD:forgechat-tools v1.0 -->

