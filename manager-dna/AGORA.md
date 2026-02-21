# AGORA.md — Engram Navigation Manual

**Purpose:** Teach every agent how to use Engrams (the Agora knowledge base) without overloading context. Lean skills, targeted concept pulls, and lessons keep work precise.

---

## 1. Engram Anatomy
```
engrams/<topic>/
├── _index.md        # Map of content + variables in play
├── SKILL.md         # Lean, canonical procedure (no branching logic)
├── concepts/
│   ├── <variant>.md # Instructions keyed to known variables (utility, finance partner, product flavor, region, etc.)
├── lessons/
│   ├── <case>.md    # Edge cases, post-mortems, SME clarifications
└── assets/ (opt)    # Reference docs, screenshots, data files
```

- **SKILL.md** stays short and linear. It references decision points but never embeds giant truth tables.
- **Concept files** store the variant-specific guidance (e.g., `concepts/coned.md`, `concepts/igs-energy.md`).
- **Lessons** capture weird cases or SME walk-throughs so we never solve the same edge case twice.

---

## 2. Execution Workflow
1. **Open `_index.md`:** confirm you have the correct Engram and understand the available concepts/lessons.
2. **Read `SKILL.md`:** follow the numbered steps exactly; this is your “plan before acting.”
3. **Inject Concepts Just-in-Time:** whenever the SKILL references a variable (`utility`, `finance_partner`, `region`, etc.), load only the matching concept file(s). Example:
   - Task: Submit Interconnection → Step 2 says “Determine utility + financing requirements.”
   - Variables: `utility=ConEd`, `finance=IGS`.
   - Action: load `concepts/coned.md` and `concepts/igs.md`, inject the YAML/markdown instructions, execute, then discard.
4. **Consult Lessons for Edge Cases:** if the step (or your intuition) suggests a known issue, load the relevant lesson file and follow its guidance.
5. **Delegate with Context Packs:** when spinning up sub-agents, give them only the SKILL step they own plus the exact concept/lesson snippets they need. Never dump the entire Engram.
6. **Log Outputs:** add results and links back to Forge tasks; note any deviations.

---

## 3. Authoring & Maintaining Engrams
- **Keep SKILL.md minimal.** If it grows beyond ~100 lines, break the process into sub-Engrams.
- **Structure concepts consistently.** Each concept file should start with frontmatter (variables, effective date, owner) followed by actionable instructions.
- **Lessons are append-only.** Include date, author, scenario, fix, and references to Forge tasks or transcripts.
- **Cross-link.** `_index.md` should list available concepts/lessons so agents know what variants exist.
- **Version control.** Treat Engrams like code: PRs, reviews, and commits referencing Forge tasks.

---

## 4. Adding a New Lesson (Novel Task Flow)
1. Capture SME guidance live (notes or recording).
2. Execute the fix while documenting exact commands/decisions.
3. Create `lessons/<slug>.md`:
   - Frontmatter: `date`, `author`, `trigger`, `variables`, `related_tasks`.
   - Body: scenario, resolution steps, verification, follow-up actions.
4. Reference the lesson from `_index.md` so future agents can find it.
5. Log the addition in MEMORY.md and link to the relevant Forge task.

---

## 5. Quality Expectations
- **No context bloat:** only load what the current step requires.
- **Deterministic execution:** SKILL + concept combo should remove ambiguity.
- **Feedback loop:** every resolved edge case becomes a lesson; every outdated concept gets pruned.
- **Traceability:** Engram changes tie back to Forge tasks and are summarized in daily memory entries.

---

> **Reminder:** Engrams are the source of truth for Tier 3 work. Use them surgically, keep them lean, and continuously feed them with new lessons so complex tasks stay solvable.
