# Claude Instructions

This file provides Claude-specific guidance for working with this repository.

---

## Core References

Before starting any task, load these foundational documents:

| Document | Purpose | When to Load |
|----------|---------|--------------|
| `AGENTS.md` | Canonical agent workflow & state machine | Every session (mandatory) |
| `memory-bank/projectbrief.md` | Project vision and goals | Session start |
| `memory-bank/systemPatterns.md` | Architecture patterns | Before architectural changes |
| `memory-bank/activeContext.md` | Current sprint focus | Every session |
| `CONTRIBUTING.md` | Contribution guidelines | Before making changes |

---

## Session Startup Checklist

> [!IMPORTANT]
> Complete this before taking any action.

```markdown
- [ ] Load `AGENTS.md` — review state machine and compliance rules
- [ ] Load `memory-bank/projectbrief.md` — understand project goals
- [ ] Load `memory-bank/systemPatterns.md` — know established patterns
- [ ] Load `memory-bank/activeContext.md` — understand current sprint
- [ ] Review task contract — clear objectives and acceptance criteria
- [ ] Output COMPLIANCE CONFIRMED statement (see AGENTS.md §1)
```

---

## Key Constraints

| Constraint | Requirement |
|-----------|-------------|
| **No Creation Without Analysis** | Search codebase first, justify why extension impossible |
| **No Rewrites** | Prefer refactoring; justify why incremental change won't work |
| **No Generic Advice** | Always cite `file:line`, show concrete integration points |
| **Architecture-First** | Load patterns before changes; extend existing services |
| **Approval Gates** | No file changes without explicit user approval |
| **Sandbox First** | Work in branches/temp clones, never touch main directly |
| **Context Engineering** | Keep working context focused on current task |

---

## State Machine Quick Reference

```
PLAN → BUILD → DIFF → QA → APPROVAL → APPLY → DOCS
  ↑                      ↑                          ↑
  └──────────────────────┴──────────────────────────┘
              [Return on changes needed]
```

**Key States**:
- **PLAN**: Output implementation plan for approval
- **BUILD**: Make changes in sandbox (branch), generate diff
- **DIFF**: Present rationale + diff with MB citations
- **QA**: Run tests, verify coverage, confirm build success
- **APPROVAL**: Wait for explicit user approval (human gate)
- **APPLY**: Apply changes to sandbox
- **DOCS**: Create task docs, update Memory Bank

---

## Reuse Validation (Before Creating Any File)

> [!WARNING]
> Complete this checklist. Never skip.

```markdown
**Files Analyzed**:
- [ ] `file1.ext` — Cannot extend: [specific technical reason]
- [ ] `file2.ext` — Cannot extend: [specific technical reason]

**Pattern Checked**: `systemPatterns.md#[section]`

**Justification**: New file needed because [exhaustive reasoning]
```

If you cannot provide specific technical reasons, the file probably shouldn't be created.

---

## Memory Bank Management

### Read Paths (Frequent)

- Session startup: Full load per complexity level
- Before architectural changes: Load `systemPatterns.md`
- When uncertain about patterns: Check `projectRules.md`

### Write Paths (Requires User Approval)

> [!NOTE]
> These updates require explicit user approval:

- `memory-bank/tasks/*/` — Task documentation (after code approval)
- `memory-bank/tasks/*/README.md` — Monthly summaries
- `memory-bank/decisions.md` — Architectural decisions
- `memory-bank/projectRules.md` — New patterns discovered
- **Any commits to version control**

These do NOT require approval:
- App code changes
- Test changes
- Configuration updates
- Operational logs

---

## Citation Standards

Always cite your sources in code and documentation:

### Code Citations
```
✅ "Extended `services/auth.ext:45` following `systemPatterns.md#Service Extension Pattern`"
✅ "Modified `file.ext:42-58` to integrate with `component.ext:120`"
❌ "Updated per systemPatterns.md" (too vague)
```

### Memory Bank Citations
```
✅ `memory-bank/systemPatterns.md#Architecture`
✅ `memory-bank/decisions.md#2025-09-15-strategy`
✅ `memory-bank/tasks/2025-10/251025_task-name.md`
❌ "systemPatterns" (incomplete)
```

---

## Task Execution Flow

### 1. PLAN State

**Output**:
```markdown
## Plan: [Task Name]

**Analyzed Files**:
- `path/file.ext:50-100` - Current implementation of X
- `memory-bank/systemPatterns.md#Pattern` - Established pattern

**Reuse Strategy**:
- Extend `file.ext` - Add method for [functionality]
- Cannot reuse [component] because: [specific technical reason]

**Implementation Steps**:
1. [Action] - extends pattern at `file:line`
2. [Action] - integrates with [component]
3. [Action] - adds tests

**Tests**: Unit: [scenarios] | Integration: [flows] | Manual: [paths]
```

**Exit**: User responds "approved", "proceed", or "looks good"

### 2. BUILD State

- Work in branch/temp clone (never main)
- Create/modify files per approved plan
- Implement minimal changes achieving objective
- Add tests alongside implementation
- Generate unified diff
- **DO NOT APPLY YET**

### 3. DIFF State

Present changes with clear rationale:
```markdown
## Proposed Changes

**Files**:
path/file1.ext    | 50 +++++++++---------
path/file2.ext    | 120 +++++++++++++++++++
3 files, 370 insertions(+), 10 deletions(-)

**Rationale**:
- Modified per `systemPatterns.md#Pattern`
- Tests mirror `existing_test.ext`

**Integration**: `component.ext:45` calls new method
```

### 4. QA State

```markdown
## QA Results

**Tests**: ✅ PASS | 145/145 | Duration: 23.5s
**Linter**: ✅ PASS | 0 errors
**Coverage**: 87.3% (+2.1%)
**Build**: ✅ SUCCESS

**Verdict**: ✅ Ready for APPROVAL
```

### 5. APPROVAL State

> [!IMPORTANT]
> Human gate — wait for explicit approval before proceeding.

Wait for user to say: "approved", "looks good", "document it", "apply it", "ship it"

### 6. APPLY State

Apply all changes to sandbox branch. Verify success or rollback.

### 7. DOCS State

> [!CRITICAL]
> Only enter after user approved code changes.

Create:
- `memory-bank/tasks/YYYY-MM/DDMMDD_task-name.md` — Task documentation
- Update `memory-bank/tasks/YYYY-MM/README.md` — Monthly summary
- Update `projectRules.md` if new patterns
- Update `decisions.md` if architectural decisions
- Update `toc.md` if new MB files

---

## Troubleshooting

### Stall Detection

**Condition**: Two consecutive identical diffs

**Response**:
```markdown
## STALL DETECTED

⚠️ Two identical diffs - unable to progress

**Diagnosis**: [technical reason]
**Recommendation**: 
1. Load more MB context
2. Try alternative approach
3. Request agent swap

**Request**: Provide direction
```

### Context Exceeded

- State already persisted to Memory Bank (via Compaction Protocol)
- Drop Task Context, reload only what's needed
- Resume from saved state in `activeContext.md`

### Agent Stuck (Cycles ≥ 3)

1. Check cycle count
2. Detect identical diffs
3. Load more Memory Bank context
4. Break into smaller subtasks
5. Request user intervention

---

## Quick Checklist

Before every major action:

- [ ] Reuse validated (searched files, justified why new)
- [ ] MB context loaded appropriate to complexity
- [ ] Citations included (`file:line`, `file.md#Section`)
- [ ] Approval gates respected (never apply without OK)
- [ ] Tests planned before BUILD
- [ ] Error handling reviewed
- [ ] Security implications considered

---

## Essential Links

- **State Machine**: `AGENTS.md §4`
- **Task Contract**: `AGENTS.md §5`
- **Memory Bank Structure**: `AGENTS.md §3`
- **Quality Standards**: `AGENTS.md §6`
- **Contributing**: `CONTRIBUTING.md`
- **Project Brief**: `memory-bank/projectbrief.md`
- **System Patterns**: `memory-bank/systemPatterns.md`

---

**Start every session with AGENTS.md. End with clarity. Build with intention.**
