# HEARTBEAT.md

<!-- FORGE:MANAGED:heartbeat-core v4.0 -->
## Every Heartbeat

This runs in your **main session** every 30 minutes. You have full access to your DNA files, skills, memory, and tools. The Forge Status cron handles reporting your status to Forge separately.

**If you are currently working on a task, keep working. Do not interrupt yourself.**

If you are idle:

### 1. Check Messages

Check configured channels for unread messages:
- **iMessage** — `imsg history --chat-id <id> --limit 5 --json`
- **ForgeChat** — `GET /api/v1/chat/conversations` with Bearer token, check for `unread_count > 0`

**If unread_count > 0: fetch and READ the actual messages.** Counting is not reading. Then respond to anything that needs a response. Do not mark messages as "already addressed" unless you have actually read and responded to them in a prior heartbeat.

### 2. Check Forge for Tasks

Query for new assignments: `GET /api/v1/tasks?assigned_to={your_agent_id}&status=todo`

### 3. Nothing Needs Attention

If no new messages or tasks, reply `HEARTBEAT_OK`.

### 4. Connection Failures

If any API call or CLI command fails during this heartbeat:
- **Do not retry.** Log the failure and move on to the next check.
- **Log it:** Append a line to `memory/connection-failures.md` with timestamp, service name, and error.
- **If 3+ consecutive heartbeats have failures for the same service**, alert your manager on the next available channel with a summary: what's down, since when, and how many failures.
- **Never let a downed API block the entire heartbeat.** Check what you can, skip what you can't.
<!-- /FORGE:MANAGED:heartbeat-core -->

<!-- FORGE:MANAGED:heartbeat-sync v1.0 -->
## Status Reporting (Self-Healing)

1. **Run forge-sync:** This reports your context usage and active cron jobs to Forge. If your configuration is out of sync, this script will auto-repair your crons.
```bash
# Get context usage first
CONTEXT_PCT=$(session_status --json | jq .context_pct)
# Run sync
cd ~/.openclaw/workspace && FORGE_EMAIL="rex@venturehome.com" FORGE_PASSWORD="rex-forge-2026" AGENT_ID="3d2c956e-038e-489d-82d2-8973e8f436e8" CONTEXT_PCT="${CONTEXT_PCT}" bash forge-skills/forge-sync/forge-sync.sh heartbeat
```
<!-- /FORGE:MANAGED:heartbeat-sync -->
