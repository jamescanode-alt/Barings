# Claude Code — Universal Instructions

> **Philosophy:** These instructions optimize Claude Code for maximum effectiveness across any project. They follow GEPA's "Actionable Side Information" pattern — telling you *what* to do, *why* things fail, and *how* to fix them.

---

## MANDATORY: Farther Design & Data-Display Standards

**Any UI, page, chart, table, or marketing copy in this project MUST follow the Farther standards. Read the source before designing or writing copy — do not work from memory.**

### Canonical references (in this repo)

| File | Use it for |
|------|-----------|
| [`FARTHER_DESIGN_SYSTEM.md`](FARTHER_DESIGN_SYSTEM.md) | Active design rules, color roles, type, voice, next-UI-update path |
| [`FARTHER_DATA_DISPLAY_STANDARD.md`](FARTHER_DATA_DISPLAY_STANDARD.md) | Canonical charts/tables/KPI components and brand notes |
| [`DATA_DISPLAY_MIGRATION_STATUS.md`](DATA_DISPLAY_MIGRATION_STATUS.md) | What's migrated vs. outstanding |
| [`farther-design-system/`](farther-design-system/) | Full brand kit: `colors_and_type.css`, `fonts/`, `assets/`, `preview/`, `ui_kits/`, `SKILL.md` |

### Non-negotiable rules

- **Tokens, not hardcoded values.** Import `farther-design-system/colors_and_type.css` (or mirror via `theme.ts`); never invent a new color/chart/table palette.
- **Color roles.** Limestone 50 `#F8F4F0` is the default canvas (not white); Charcoal 900 `#333333` for primary text (never pure `#000`); Steel Blue 700 `#3B5A69` is the brand lock. White is a card/clarity surface only. Aqua/Pomegranate for positive/negative data states only. Bronze sparingly. No purple. Ratio ≈ 70% primary / 25% secondary / 5% accent.
- **Type.** ABC Arizona Text for headlines, titles, and numerals; Fakt Pro for body, UI, eyebrows, controls, CTAs.
- **Copy.** Sentence case; no terminal period on single-sentence headlines; "and" not "&"; Oxford commas. Category = "Intelligent Wealth Management", product = "Intelligent Wealth Platform". Clients = "modern wealth builders"; advisors = "elite/expert advisors". No emoji. Voice: proactive, precise, empowering. (Note: the brand guide permits a spaced em dash for emphasis — but the user's global anti-slop rule bans em dashes in user-visible copy. **Honor the global rule: use a period, comma, or colon instead.**)
- **Data display.** Import from `@/components/data-display` (or the documented primitives); never recreate or use default chart/table-library styling. Flat surfaces, hairline borders, soft rounded corners, quiet trends, calm `easeWave` motion. Design loading/empty/no-data/filtered/selected/hover states with equal care. **Real data or empty states only — never mock data.**
- **Compliance.** Flag and correct outdated, misleading, or non-compliant financial claims rather than implementing verbatim. Never fabricate testimonials, names, or statistics.

---

## MANDATORY: Project Execution Rules

**These rules are ABSOLUTE. Never skip them.**

### Project Isolation (Critical)

- ALL work MUST stay inside the current project folder
- NEVER pull code, copy files, or import from other projects on this machine
- NEVER search outside the active project directory
- Treat every repository as fully isolated

### Required Project Files

Every project must maintain these files in the root:

| File | Purpose | Update When |
|------|---------|-------------|
| `PLAN_LOG.md` | Task planning and objectives | BEFORE starting any coding |
| `CHANGE_LOG.md` | Record of completed changes | AFTER every push to GitHub |
| `TODO.md` | Bugs, follow-ups, improvements | Whenever discovered |

### Session Workflow (Follow This Order)

```
1. UPDATE PLAN_LOG.md (date, task, objective, files, risks, next steps)
2. REVIEW TODO.md (check existing items)
3. DO THE WORK (strictly inside current repo)
4. VALIDATE (lint, typecheck, tests, build, deployment-ready)
5. UPDATE TODO.md (add anything discovered)
6. PUSH TO MAIN (required after every task — no exceptions)
7. UPDATE CHANGE_LOG.md (summary, files, tests, status, issues)
8. CONTINUE TODO items (don't ask "what next?" if items exist)
```

### Push to Main (Mandatory After Every Task)

**ALWAYS push to main when a task is complete.** This is non-negotiable.

```bash
git add <specific files>                          # never git add .
git commit -m "<type>: <description>"             # conventional commit format
git push origin main                              # push immediately after commit
```

- Push after EVERY completed task — do not batch multiple tasks before pushing
- Never leave completed work uncommitted
- If push fails (lock, auth, network), surface the exact commands for the user to run manually
- Update CHANGE_LOG.md before or immediately after the push

### Pre-Push Verification (Required)

**NEVER push code that hasn't been validated.** Run ALL applicable checks:

- [ ] Dependency install works
- [ ] Lint passes
- [ ] Typecheck passes
- [ ] Tests pass
- [ ] Build succeeds
- [ ] Env/config validated
- [ ] Startup/runtime sanity check

**Goal:** Prevent failed deployments BEFORE code reaches GitHub.

### Continue Through TODO

- When current task is complete, continue working TODO items
- DO NOT stop and ask "what next?" when actionable items exist
- Only stop when all items are done, blocked, or documented

---

## Prime Directives

1. **Understand before acting** — Read files, check patterns, ask if unclear
2. **Minimal changes** — Do exactly what's asked, nothing more
3. **Security first** — Never introduce vulnerabilities
4. **Verify outcomes** — Run tests, check results, confirm success
5. **Stay in project** — Never use code from other projects

---

## Pre-Task Protocol

**Before writing ANY code:**

```
1. UNDERSTAND → What is the actual goal? Ask if ambiguous.
2. EXPLORE    → Glob/Grep for existing patterns. Never reinvent.
3. READ       → Always read files before editing them.
4. PLAN       → For complex tasks, outline approach first.
5. EXECUTE    → Make minimal, focused changes.
6. VERIFY     → Run tests, check for errors, confirm outcome.
```

---

## Decision Framework

### Ask vs. Proceed

```
Is the request ambiguous?
├─ YES → ASK: "Do you want X or Y?"
├─ NO  → PROCEED with the clear interpretation
└─ UNCERTAIN → STATE ASSUMPTION: "I'll do X. Say if you want Y."
```

### Plan vs. Execute

```
Task complexity?
├─ TRIVIAL: Single line fix, typo         → Execute immediately
├─ SIMPLE: One file, clear change         → Execute directly
├─ MEDIUM: 2-5 files, known pattern       → Brief outline, then execute
└─ COMPLEX: 5+ files, new architecture    → Enter Plan Mode
```

### Which Tool

```
Find files?
├─ By name/pattern  → Glob("**/*.py")
├─ By content       → Grep("function_name")
└─ Broad search     → Task(Explore agent)

Modify files?
├─ Small edit       → Edit
├─ New file         → Write
└─ Multiple edits   → Parallel Edit calls

Run commands?
├─ File ops         → Read/Write/Edit/Glob/Grep (NOT Bash)
├─ Git/npm/build    → Bash
└─ System commands  → Bash
```

---

## Quality Gates

### Before Every Change

- [ ] Read the file first
- [ ] Understood existing patterns
- [ ] Change is minimal and focused
- [ ] No hardcoded secrets
- [ ] No security vulnerabilities

### Before Marking Complete

- [ ] Requested change is implemented
- [ ] Tests pass (if they exist)
- [ ] No new errors introduced
- [ ] User can verify the result

---

## Failure Patterns & Fixes

### "File not found" / "Method doesn't exist"

**Cause:** Assumed structure without reading first.
**Fix:** Always `Glob` to find files, `Grep` to find code, `Read` before `Edit`.

### "Tests failing after change"

**Cause:** Changed behavior without understanding expectations.
**Fix:** Read test files first. Run tests before AND after changes.

### "Over-engineered solution"

**Cause:** Added unrequested features, refactoring, "improvements."
**Fix:** Do ONLY what was asked. Stop when the specific request is done.

### "Type errors"

**Cause:** Wrong types, missing null checks, `any` usage.
**Fix:** Add explicit types. Use `unknown` not `any`. Handle nulls.

### "Security vulnerability introduced"

**Cause:** String concatenation in SQL, unsanitized input, hardcoded secrets.
**Fix:** Parameterized queries, input validation, environment variables.

### "Build works locally but fails in CI"

**Cause:** Missing dependencies, different versions, uncommitted files.
**Fix:** Check CI logs, compare environments, ensure all files committed.

---

## Core Behaviors

### 1. Minimal Changes (Critical)

**DO:** Change only what's requested.
**DON'T:** Refactor nearby code, add docstrings, "improve" while you're there.

```
User: "Fix the typo on line 42"

✓ GOOD: Edit line 42 only
✗ BAD:  Also reformat file, add types, improve naming
```

### 2. Read Before Edit (Critical)

**ALWAYS** read a file before modifying it. This prevents:
- Overwriting important code
- Missing existing patterns
- Duplicating functionality
- Breaking dependencies

### 3. Security First

Check for these before ANY commit:
- Hardcoded API keys, passwords, tokens → Use env vars
- SQL string concatenation → Parameterized queries
- User input in shell commands → Escape or reject
- User input in HTML → Sanitize

### 4. Follow Existing Patterns

When adding code to an existing project:
1. Find similar existing code
2. Match its style, structure, naming
3. Don't introduce new patterns unnecessarily

---

## Parallel Execution

### DO Parallelize

- Reading multiple independent files
- Searching with multiple patterns
- Independent edits to different files
- Independent tool calls

### DON'T Parallelize

- Calls where one depends on another's result
- Multiple edits to the same file
- Sequential operations (git add → commit → push)

```python
# GOOD: Parallel reads
Read(file1.py) + Read(file2.py) + Read(file3.py)

# GOOD: Parallel searches
Grep("pattern1") + Glob("**/*.ts")

# BAD: Sequential dependency - must be separate calls
result = Read(config.json)  # First
Edit(config.json, based_on_result)  # Then
```

---

## Git Protocol

### Commit Format

```
<type>: <description>

Types: feat, fix, refactor, docs, test, chore, perf, ci
```

### Safety Rules (Never Break These)

- **NEVER** use `--no-verify` (skips hooks)
- **NEVER** force push to main/master without explicit permission
- **NEVER** amend commits unless explicitly asked
- **NEVER** use `git add .` — stage specific files
- **ALWAYS** create NEW commits after hook failures (not amend)

### When Pre-Commit Hook Fails

```
Hook failed → Fix the issue → Stage fix → NEW commit (not amend)
```

The original commit didn't happen. Amending would change the PREVIOUS commit.

---

## Language Guidelines

### Universal Rules

| Rule | Why |
|------|-----|
| Explicit types | Catches errors early, self-documents |
| Handle errors | Silent failures cause debugging nightmares |
| No magic values | Use constants or config |
| Validate inputs | Trust nothing from outside your system |
| Log important events | Debugging requires visibility |

### Python

```python
# Naming
variable_name = "snake_case"
CONSTANT = "SCREAMING_SNAKE"
def function_name(): pass
class ClassName: pass

# Always use
- Type hints on functions
- Context managers for resources
- logging module (not print)
- Explicit encoding for files
```

### TypeScript/JavaScript

```typescript
// Types
const value: string = "typed";
function fn(arg: number): Result {}

// Never use 'any' — use 'unknown' instead
const bad: any = data;     // ✗
const good: unknown = data; // ✓

// Explicit nulls
const result: User | null = data ?? null;
```

### Go

```go
// Handle all errors explicitly
result, err := doSomething()
if err != nil {
    return fmt.Errorf("context: %w", err)
}

// No naked returns in functions with named return values
```

---

## Agent Delegation

Use specialized agents for complex tasks:

| Situation | Agent |
|-----------|-------|
| Complex feature planning | `planner` |
| Code just written | `code-reviewer` |
| Security-sensitive code | `security-reviewer` |
| Build failures | `build-error-resolver` |
| Writing tests first | `tdd-guide` |
| Broad codebase search | `Explore` |
| Architecture decisions | `architect` |

**Parallel agents:** Launch multiple agents simultaneously for independent analyses.

---

## Common Operations

### Adding a Feature

```
1. Glob for similar features → understand patterns
2. Read related files → understand context
3. Plan approach (if complex)
4. Implement with minimal changes
5. Run existing tests
6. Add tests for new code (if project has tests)
```

### Fixing a Bug

```
1. Reproduce/understand the bug
2. Find root cause (not just symptoms)
3. Read surrounding code
4. Fix with minimal change
5. Verify fix works
6. Check for similar bugs elsewhere
```

### Refactoring

```
1. Understand current behavior completely
2. Ensure tests exist (or add them first)
3. Make incremental changes
4. Test after each change
5. Stop when requested scope is done
```

---

## Error Handling Patterns

### Try/Catch with Context

```python
# Python
try:
    result = risky_operation()
except SpecificError as e:
    logger.error(f"Operation failed: {e}", exc_info=True)
    raise  # or handle appropriately
```

```typescript
// TypeScript
try {
  const result = await riskyOperation();
} catch (error) {
  logger.error("Operation failed", { error });
  throw error; // or handle appropriately
}
```

### Fail Fast on Bad Input

```python
def process(data: dict) -> Result:
    if not data:
        raise ValueError("data cannot be empty")
    if "required_field" not in data:
        raise ValueError("missing required_field")
    # ... proceed with valid data
```

---

## API Integration Patterns

### Retry with Backoff (Required for external APIs)

```python
def call_with_retry(fn, max_attempts=3):
    for attempt in range(max_attempts):
        try:
            return fn()
        except (RateLimitError, ServerError):
            if attempt == max_attempts - 1:
                raise
            time.sleep(2 ** attempt)  # 1s, 2s, 4s
```

### Environment Variables

```python
# Validate at startup, not on-demand
def load_config():
    required = ["API_KEY", "DATABASE_URL"]
    missing = [k for k in required if not os.getenv(k)]
    if missing:
        raise ValueError(f"Missing: {missing}")
```

---

## Testing Philosophy

### When Tests Exist

- Run them before making changes
- Run them after making changes
- Don't modify tests to make them pass (unless they're wrong)
- Add tests for new functionality

### When No Tests Exist

- Don't add tests unless asked
- Focus on manual verification
- Be extra careful with changes

---

## Project Discovery

When starting in a new project:

```
1. Read README.md (if exists)
2. Read CLAUDE.md (if exists)
3. Check package.json / pyproject.toml / go.mod for stack
4. Glob for project structure
5. Identify existing patterns before adding code
```

---

## Communication Style

- **Concise** — No unnecessary words
- **Specific** — Reference files as `path/file.py:42`
- **Honest** — Say "I don't know" when uncertain
- **Ask** — Clarify ambiguity before guessing

---

## Success Criteria

**A task is COMPLETE when:**

✅ The specific request is fulfilled
✅ No new bugs introduced
✅ No security issues added
✅ Follows existing project patterns
✅ User can verify the outcome

**A task is NOT complete if:**

❌ Tests are failing
❌ Build is broken
❌ Unrelated changes were made
❌ Security vulnerabilities exist

---

## Final Checklist (Every Response)

1. Did I update PLAN_LOG.md before starting?
2. Did I stay inside the current project only?
3. Did I read files before editing?
4. Did I make minimal, focused changes?
5. Did I check for security issues?
6. Did I validate before pushing?
7. Did I update CHANGE_LOG.md after pushing?
8. Did I add discovered items to TODO.md?
9. Can the user verify the result?

**If any answer is "no" → stop and address it.**

---

## Non-Compliance Rule

**These rules are MANDATORY, not optional.**

- NEVER skip logs, TODO updates, or deployment validation
- NEVER use other projects as source material
- NEVER push without pre-validation
- In any conflict, project execution rules take priority unless user explicitly overrides

**Failure to follow these rules invalidates the work.**

---

## User Environment & Preferences

### Software
- **No Microsoft PowerPoint installed** — use Google Slides instead
  - Default for shareable presentations: create `.pptx` files — Google Slides imports them via File → Import slides
  - Use HTML presentations only for browser-hosted tools, Railway-deployed pages, or internal dashboards (not for Drive sharing)
- **Spreadsheets:** confirm whether Google Sheets or Excel is preferred before creating spreadsheet files

---

## Session Initialization & Tool Integration

### Session Startup Protocol

At the start of each coding session:

1. **Run silent CLI check** - verify kimi, gh, dbt, pgcli, csvkit, railway are available
2. **Check authentication** - if using GitHub, verify `gh auth status`
3. **Git status** - if in a repo, check branch and uncommitted work
4. **Report issues only** - don't spam if everything is working

### Tool Integration Preferences

**For AI coding tasks:**
- **First choice**: `/kimi:write` (K2.6 for complex coding tasks)
- **Second choice**: `/cursor:write` (for bulk edits and refactoring)
- **Planning**: `/kimi:plan` or `/cursor:plan` for architectural design
- **Research**: `/gemini:research` for deep research with large context windows
- **Code review**: `/copilot:review` for GitHub-aware code review

**For data pipeline tasks:**
1. **Validate CSVs** with `csvkit` before import
   ```bash
   csvstat billing_export.csv
   csvcut -c account_number,balance,status data.csv | csvgrep -c status -m "active"
   ```
2. **Transform** with `dbt run --select <model>`
3. **Query results** with `pgcli` (better than psql)
   ```bash
   pgcli postgresql://localhost/farther_crm
   ```

**For GitHub workflow:**
1. **Check auth** first: `gh auth status`
2. **Create PRs**: `gh pr create --fill`
3. **List issues**: `gh issue list`
4. **Never use web UI** when CLI available

**For database operations:**
- **Prefer `pgcli`** over `psql` for interactive queries (autocomplete, syntax highlighting)
- Use parameterized queries to prevent SQL injection
- Always validate connection before running migrations

### Tool Selection Matrix

| Task Type | Primary Tool | Fallback | Notes |
|-----------|-------------|----------|-------|
| AI Coding | `/kimi:write` | `/cursor:write` | Use Kimi K2.6 for complex tasks |
| Planning | `/kimi:plan` | `/cursor:plan` | Read-only design mode |
| Research | `/gemini:research` | `/kimi:research` | 1M token context for deep dives |
| Code Review | `/copilot:review` | manual review | GitHub context aware |
| CSV Processing | `csvkit` | `pandas` | Validate before DB import |
| SQL Queries | `pgcli` | `psql` | Interactive with autocomplete |
| GitHub PRs | `gh pr create` | web UI | CLI for automation |
| Data Transform | `dbt run` | manual SQL | Staging → production |
| Deployments | `railway up` | web UI | CLI for CI/CD |

### Critical Environment Variables

Before deployment tasks, verify these are set:

- `DATABASE_URL` - Postgres connection string
- `BIGQUERY_PROJECT` - GCP project ID for BigQuery
- `MINIMAX_API_KEY` - MiniMax API authentication (if using MiniMax)
- `RAILWAY_TOKEN` - Railway deployment token (if deploying via CLI)

**Do not proceed with deployment if any critical variables are missing.**

### Available CLI Tools

**AI & Coding:**
- Kimi CLI (K2.6) - `kimi` - `/kimi:write`, `/kimi:plan`, `/kimi:research`
- Cursor - `agent` - `/cursor:write`, `/cursor:plan`, `/cursor:debug`
- Copilot - `copilot` - `/copilot:review`, `/copilot:research`
- Gemini - `gemini` - `/gemini:research`, `/gemini:explore`
- Qwen - `qwen` - `/qwen:write`
- MiniMax - `mmx` - Text, image, video, speech, music generation

**Data & Database:**
- csvkit - `csvstat`, `csvcut`, `csvgrep`, `csvsql`, `csvjoin`
- dbt - `dbt run`, `dbt test`, `dbt docs generate`
- pgcli - `pgcli postgresql://...`

**Development:**
- GitHub CLI - `gh pr`, `gh issue`, `gh repo`
- Railway CLI - `railway up`, `railway logs`
