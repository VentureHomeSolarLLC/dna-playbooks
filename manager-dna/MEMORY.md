
## Enfin TPO Financing Credit and Utility Bill Requirements (2026-02-09)

**Source:** Email from Alex Yackery (forwarded from James Reardon of Enfin) - `19c4546c4687d558`

Key details regarding Enfin's Third Party Ownership (TPO) financing:

**Credit Requirements:**
*   **FICO Score:** 620 minimum for auto-approval.
*   **Below 700 FICO:** Customer must enter 'stated income' and confirm its truthfulness (no W2 required).
*   **Credit Bureau:** TransUnion is used for TPO (no waterfall).

**Utility Bill Balances:**
*   **Delinquencies Check:** Experian is used to check for utility delinquencies.
*   **Impact:** Utility delinquencies rarely affect applications.
*   **Past Due Notices:** Fine if a utility bill has a past due notice.
*   **Significant Missed Payments:** Only significant missed payments (e.g., 10 out of 12 months) would potentially be an issue.

## 2026-02-18 — Installation Map Project Complete (Phase 1)
- Built interactive map at map.venturehome.com in one night
- 15,403 installations geocoded (14,747 exact street, 656 zip fallback, 9 skipped)
- 8 office locations with exact addresses
- Tech: Mapbox GL JS, Vite, vanilla JS, static site on GCP VM
- Features: VH logomark pins, yellow glow halos, satellite toggle, state filter, popups with street name
- GitHub: VentureHomeSolarLLC/map, auto-deploys via GitHub Actions
- Emailed Chris and AJ (ajinkya@venturehome.com) list of 665 dirty addresses for cleanup
- Alex has a "bigger idea" for an estimator tool — keep radius-based neighbor count in back pocket
- Brand colors: #231F20 (charcoal), #F7FF96 (yellow), #7AEFB1 (mint), #B1C3BD (sage), #F3F3EA (off-white)
- Brand font: Bagoss Extended/Standard (woff2 pulled from venturehome.com)
- Mapbox account: venturehomesolar (rex@venturehome.com)

## 2026-02-18 — Estimator / Venture Home App Vision (Alex brainstorm)
- NOT just an estimator — it's the front door to the Venture Home ecosystem
- Host at app.venturehome.com as a PWA (progressive web app)
- Chat-first UX like iMessage, conversational flow
- Products: solar, battery backup, EV charger, new roof, or multiple
- Ask if they have questions first (keep them engaged, prevent drop-off) but steer back to tool — it's really a fancy lead capture
- Bill upload via photo (Claude vision extracts kWh), SMS link for in-field capture
- Three accuracy tiers: avg bill, monthly values, bill photo
- Estimate not saved unless they create account/download app — incentive to stay
- Once in the app: hooks into Helios KB, appointment scheduling, Canopy CRM integration
- Show nearby VH installations from map data ("142 neighbors near you")
- Google Solar API for roof analysis
- Alex likes the word "abundant" for Venture Home — name should play on that
- Current estimator: estimate.venturesolar.com (Demand IQ / Google Project Sunroof, third-party)
- Phase 1 MVP: solar estimator + energy savings tips + book appointment
- Phase 2+: expand to full app ecosystem
- This replaces Demand IQ long-term

## 2026-02-18 — Project Abby (confirmed name)
- Estimator/app named "Abby" — short for Abundant
- Abby is the AI chat persona customers interact with
- Full spec doc due EOD Feb 18
- Deliver via email + Google Drive

## 2026-02-18 — Evening Wrap-up Execution Learnings
- **Lesson Learned: Robust JSON Handling for `curl`:** Directly embedding complex JSON with multiple levels of quotes and escapes within a shell `curl` command is prone to errors. Writing the JSON payload to a temporary file and using `curl -d @filename` is a more robust approach.
- **Decision: Daily Digest Content when Session Transcripts are Unavailable:** When unable to access full session transcripts due to tool restrictions, create daily digests based on the immediate context of the current task being performed.
- **Tool Behavior: `sessions_history` Visibility:** The `sessions_history` tool has visibility restrictions, specifically `tools.sessions.visibility=tree`, which prevents direct access to full session transcripts from the main session.

## 2026-02-19 — Project Agora / Engrams Architecture
**Source:** https://venturehomesolarllc.github.io/company-handbook/project-agora.html & /forge-2.0-agora-os.html
Major architectural shift for autonomous agents and Forge.

**Core Goal:** Move from task-completion to true autonomy via structured knowledge ("Engrams").

**Key Definitions:**
- **The Agora:** The collective library of all operational knowledge (navigable graph of Engrams).
- **Engram:** A directory-based unit of cognitive information (replaces monolithic SKILL.md).
  - Structure: `engrams/<name>/`
  - `_index.md`: Map of Content (MOC) — navigation & summary.
  - `SKILL.md`: Core procedure (lean steps).
  - `concepts/`: Static knowledge/reference files.
  - `lessons/`: Learned experiences (feedback loop).
- **The Synaptic Gap:** The failure point where an agent finds a task but lacks the specific instruction to execute it. Agora bridges this.
- **Cognitive Loop:** DNA guides the agent: Plan → Build → Verify → Test → Deliver (consulting Agora for the Plan).

**Agent Roles:**
- **Manager (e.g., Rex):** Proactive, broad scope. Orchestrates, plans, delegates. Consults full Agora.
- **Worker Bee:** Reactive, narrow scope. Executes specific Engrams with high fidelity.
- **Scribe:** Monitors execution, creates `lessons/` from feedback (PR-based learning).

**Forge 2.0 (Agora OS):**
- **Structured Tasks:** Tasks become JSON objects pointing to specific Engrams (`{ task: "Submit", engram: "interconnection", params: {...} }`).
- **Feedback Loop:** Human feedback on tasks triggers Scribe to create new lessons, closing the loop.
