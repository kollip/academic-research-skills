# Academic Research Skills Changelog

Cross-skill fixes and update history.

---

## 2026-03-08

### Full English Translation — All Skills Translated to English

**Files changed**: All `.md` files across `academic-pipeline/`, `academic-paper/`, `academic-paper-reviewer/`, `deep-research/`

**Changes**:
- Translated all Chinese content to English across 68+ files (agents, references, templates, examples, SKILL.md)
- TSSCI journal names in `top_journals_by_field.md` retain official Chinese names as proper nouns (with English translations)
- Privacy scan: removed residual `HEEACT Luminai` reference from `deep-research/references/socratic_questioning_framework.md`
- `README.zh-TW.md` intentionally kept in Chinese as the bilingual README option

---

### academic-pipeline v2.5 — External Review Protocol

**Files changed**: `academic-pipeline/SKILL.md`

**Changes**:
- New External Review Protocol section: 4-step workflow for handling real journal reviewer feedback (intake → strategic coaching → revise + Response to Reviewers → completeness check)
- Difference table: internal simulated review vs. external real review
- Strategic Revision Coaching: 4 layers (understanding → judgment → strategy → risk assessment)
- Response to Reviewers auto-generated template
- Self-verification completeness check adjustments
- Capability boundaries: AI verification ≠ real reviewer satisfaction

---

### academic-pipeline v2.4 — Stage 6 Process Summary + Collaboration Quality Evaluation

**Files changed**: `academic-pipeline/SKILL.md`, `README.md`, `README.zh-TW.md`

**academic-pipeline v2.4**:
- New Stage 6 PROCESS SUMMARY: auto-generates structured paper creation process record after pipeline completion
- Asks user preferred language (zh/en/both), generates MD → LaTeX → PDF
- Mandatory final chapter: **Collaboration Quality Evaluation** — 6 dimensions scored 1–100:
  - Direction Setting, Intellectual Contribution, Quality Gatekeeping
  - Iteration Discipline, Delegation Efficiency, Meta-Learning
- Includes: What Worked Well, Missed Opportunities, Recommendations, Human vs AI Value-Add, Claude's Self-Reflection
- Pipeline expanded from 9 to 10 stages (state machine, dashboard, audit trail updated)
- Scoring rubric: 90-100 Exceptional / 75-89 Excellent / 60-74 Good / 40-59 Basic / 1-39 Needs Improvement

**Lesson**: pandoc's newer longtable output uses `\real{}` macro which requires `\usepackage{calc}` in the LaTeX wrapper

---

### academic-pipeline v2.3 — APA 7.0 Formatting & LaTeX-to-PDF

**Files changed**: `academic-pipeline/SKILL.md`, `README.md`, `README.zh-TW.md`

**academic-pipeline v2.3**:
- Stage 5 FINALIZE now prompts user for formatting style (APA 7.0 / Chicago / IEEE) before generating LaTeX
- PDF must compile from LaTeX via `tectonic` (no HTML-to-PDF conversion allowed)
- APA 7.0 uses `apa7` document class (`man` mode) with `natbib` option (no biber required)
- XeCJK for bilingual CJK support; font stack: Times New Roman + Source Han Serif TC VF + Courier New
- Known apa7 quirks documented: `noextraspace` removed in v2.15, pandoc `\LTcaptype{none}` needs `\newcounter{none}`, `\addORCIDlink` takes ID only (not full URL)

**README updates**:
- Added Performance Notes section: recommended model Claude Opus 4.6 with Max plan; large token consumption warning
- Updated pipeline stage 5 description in both EN and zh-TW READMEs

**Lesson**: Always ask the user which academic formatting style they want (APA 7.0, Chicago, IEEE, etc.) before generating the final PDF — formatting style is a separate concern from citation style

---

## 2025-03-05

### v2.2 / v1.3 Cross-Agent Quality Alignment Update (4 skills)

**Files changed**: 19 files across 4 skills (+550 lines)

**deep-research v2.2**:
- Added cross-agent quality alignment definitions (peer-reviewed, currency rule, CRITICAL severity, source tier, minimum source count, verification threshold)
- Synthesis anti-patterns, Socratic quantified thresholds & auto-end conditions
- Reference existence verification (DOI + WebSearch)
- Enhanced ethics reference integrity check (50% + Retraction Watch)
- Mode transition matrix

**academic-paper v2.2**:
- 4-level argument strength scoring with quantified thresholds
- Plagiarism & retraction screening protocol
- F11 Desk-Reject Recovery + F12 Conference-to-Journal Conversion failure paths
- Plan → Full mode conversion protocol

**academic-paper-reviewer v1.3**:
- DA vs R3 role boundaries with explicit responsibility tables
- CRITICAL finding criteria with concrete examples
- Consensus classification (CONSENSUS-4/3/SPLIT/DA-CRITICAL)
- Confidence Score weighting rules
- Asian & Regional Journals reference (TSSCI + Asia-Pacific + OA options)

**academic-pipeline v2.2**:
- Checkpoint confirmation semantics (6 user commands with precise actions)
- Mode switching rules (safe/dangerous/prohibited matrix)
- Skill failure fallback matrix (per-stage degradation strategies)
- State ownership protocol (single source of truth with write access control)
- Material version control (versioned artifacts with audit trail)

---

## 2026-03-01

### Simplify Academic Research Skills SKILL.md (4 files)

**Motivation**: 4 academic research skills totaled 2,254 lines with significant cross-skill duplication and redundant inline content already available as template files.

**Files changed**:
- `academic-paper-reviewer/SKILL.md` (570→470, -100 lines)
- `academic-pipeline/SKILL.md` (675→535, -140 lines)
- `deep-research/SKILL.md` (469→435, -34 lines)
- `academic-paper/SKILL.md` (540→443, -97 lines)

**Changes**:
- A: Reviewer — removed inline templates, replaced with `templates/` file references (kept Devil's Advocate special format notes)
- B: Pipeline — removed ASCII state machine, replaced with concise 9-stage list + reference
- C: Pipeline — simplified Two-Stage Review Protocol to inputs/outputs/branching only
- D: 3 skills — "Full Academic Pipeline" section replaced with one-line reference to `academic-pipeline/SKILL.md`
- E: 4 skills — trimmed routing tables, removed HEI routes already defined in root CLAUDE.md
- F+G: Removed duplicate Mode Selection sections from deep-research and academic-paper
- H: academic-paper Handoff Protocol simplified to overview + upstream reference
- I: academic-paper Phase 0 Config replaced with reference to `agents/intake_agent.md`
- J: 4 skills — Output Language sections reduced to 1 line each
- K: Fixed revision loop cap contradiction (pipeline overrides academic-paper's max 2 rule)

**Result**: 2,254→1,883 lines (-371 lines, -16.5%), all 371 quality tests passed

**Lesson**: Inlining full template content in SKILL.md is unnecessary redundancy — a one-line reference suffices when template files exist at the correct path
