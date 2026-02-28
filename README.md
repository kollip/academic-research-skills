# Academic Research Skills for Claude Code

一套完整的學術研究 Claude Code 技能包，涵蓋從研究到論文出版的全流程。

A comprehensive suite of Claude Code skills for academic research, covering the full pipeline from research to publication.

---

## Features

- **Deep Research** — 10-agent research team with Socratic guided mode
- **Academic Paper** — 10-agent paper writing with chapter-by-chapter planning
- **Academic Paper Reviewer** — Multi-perspective peer review (EIC + 3 dynamic reviewers + Devil's Advocate)
- **Academic Pipeline** — Full 9-stage pipeline orchestrator with integrity verification and Socratic revision coaching

### Full Pipeline (v2.0)

```
Research → Write → Integrity Check → Review (5-person) → Socratic Coaching
  → Revise → Re-Review → Re-Revise → Final Integrity Check → Finalize
```

**v2.0 Key Improvements:**
1. Mandatory user confirmation checkpoint after every stage
2. Pre-review integrity verification — 100% reference & data validation
3. Two-stage review with Devil's Advocate
4. Socratic revision coaching between review and revision stages
5. Final integrity verification before publication
6. Output: MD + DOCX → ask LaTeX → confirm → PDF

---

## Prerequisites

### Install Node.js

Claude Code requires Node.js 18+.

```bash
# macOS (using Homebrew)
brew install node

# Windows (using winget)
winget install OpenJS.NodeJS.LTS

# Linux (using nvm)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
nvm install --lts
```

### Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

### Set Up API Key

You need an Anthropic API key. Get one at https://console.anthropic.com/

```bash
# Claude Code will prompt for your API key on first run
claude
```

Or set it as an environment variable:

```bash
export ANTHROPIC_API_KEY=sk-ant-xxxxx
```

---

## Installation

### Method 1: As Project Skills (Recommended)

Clone this repo into your project's `.claude/skills/` directory:

```bash
# Navigate to your project root
cd /path/to/your/project

# Create skills directory if it doesn't exist
mkdir -p .claude/skills

# Clone the skills
git clone https://github.com/Imbad0202/academic-research-skills.git .claude/skills/academic-research-skills
```

Then copy the `.claude/CLAUDE.md` content into your project's `.claude/CLAUDE.md` (merge with existing if you have one).

### Method 2: As a Standalone Project

```bash
# Clone the repo
git clone https://github.com/Imbad0202/academic-research-skills.git

# Navigate to the project
cd academic-research-skills

# Start Claude Code
claude
```

### Method 3: Upload to claude.ai

claude.ai 的 Project 功能可以載入這些 skills，不需要安裝 Claude Code。

**步驟：**

1. 從這個 repo 下載所有 `SKILL.md` 檔案（共 4 個）：
   - `deep-research/SKILL.md`
   - `academic-paper/SKILL.md`
   - `academic-paper-reviewer/SKILL.md`
   - `academic-pipeline/SKILL.md`

2. 登入 [claude.ai](https://claude.ai)

3. 建立新 Project：
   - 點擊左側欄 **Projects** → **Create Project**
   - 命名為「Academic Research」（或任意名稱）

4. 上傳 SKILL.md 檔案：
   - 進入 Project → 點擊 **Project Knowledge**（右側面板）
   - 點擊 **Add Content** → **Upload Files**
   - 上傳 4 個 `SKILL.md` 檔案

5. （選用）上傳 reference 和 template 檔案以獲得更好效果：
   - `deep-research/references/` 下的檔案（APA 指南、方法論模板等）
   - `academic-paper/references/` 下的檔案（引用格式、寫作風格等）
   - `academic-paper/templates/` 下的檔案（論文結構模板）

6. 開始對話：在 Project 中開啟新對話，直接說「引導我研究 X」或「幫我寫論文」

**claude.ai 限制：**
- Project Knowledge 檔案大小上限為每個檔案 200KB
- SKILL.md 的 YAML frontmatter 中 `version` 和 `last_updated` 必須在 `metadata:` 下，否則上傳會失敗
- claude.ai 不支援多 agent 平行執行，效果不如 Claude Code 完整
- 建議至少上傳 4 個 SKILL.md + 核心 references，以獲得最佳效果

---

## Usage

### Quick Start

```
# Start a full research pipeline
You: "我想做一篇關於 AI 對高教品保影響的研究論文"

# Start with Socratic guidance
You: "引導我研究 AI 在教育評鑑中的應用"

# Write a paper with guided planning
You: "引導我寫一篇關於少子化影響的論文"

# Review an existing paper
You: "幫我審查這篇論文" (then provide the paper)

# Check pipeline status
You: "進度" or "status"
```

### Individual Skills

#### Deep Research
```
"Research the impact of AI on higher education" → full mode
"引導我研究 X" → socratic mode (guided)
"幫我查核這些說法" → fact-check mode
"幫我做文獻回顧" → lit-review mode
```

#### Academic Paper
```
"幫我寫一篇論文" → full mode
"引導我寫論文" → plan mode (guided)
"幫我轉換格式成 LaTeX" → format-convert mode
"檢查引用格式" → citation-check mode
```

#### Academic Paper Reviewer
```
"審查這篇論文" → full mode (EIC + R1/R2/R3 + Devil's Advocate)
"引導我改進這篇論文" → guided mode
"檢查研究方法" → methodology-focus mode
"驗收修訂" → re-review mode
```

#### Academic Pipeline (Orchestrator)
```
"我想做一篇完整的研究論文" → full pipeline from Stage 1
"我已經有論文，幫我審查" → mid-entry at Stage 2.5 (integrity first)
"我收到審稿意見了" → mid-entry at Stage 4
```

### Supported Languages

- **Traditional Chinese** (繁體中文) — default when user writes in Chinese
- **English** — default when user writes in English
- Bilingual abstracts (中文 + English) for academic papers

### Supported Citation Formats

- APA 7.0 (default, including Chinese citation rules)
- Chicago (Notes & Author-Date)
- MLA
- IEEE
- Vancouver

### Supported Paper Structures

- IMRaD (empirical research)
- Thematic Literature Review
- Theoretical Analysis
- Case Study
- Policy Brief
- Conference Paper

---

## Skill Details

### Deep Research (v2.0)

10-agent pipeline for rigorous academic research:

| Agent | Role |
|-------|------|
| Research Question Agent | FINER-scored RQ formulation |
| Research Architect | Methodology design |
| Bibliography Agent | Systematic literature search |
| Source Verification Agent | Evidence grading, predatory journal detection |
| Synthesis Agent | Cross-source integration |
| Report Compiler | APA 7.0 report drafting |
| Editor-in-Chief | Q1 journal editorial review |
| Devil's Advocate | Assumption challenging (3 checkpoints) |
| Ethics Review Agent | AI disclosure, attribution integrity |
| **Socratic Mentor** | **Guided research dialogue (new in v2.0)** |

### Academic Paper (v2.0)

10-agent pipeline for academic paper writing:

| Agent | Role |
|-------|------|
| Intake Agent | Configuration interview + handoff detection |
| Literature Strategist | Search strategy + annotated bibliography |
| Structure Architect | Paper outline + word allocation |
| Argument Builder | Thesis + claim-evidence chains |
| Draft Writer | Section-by-section writing |
| Citation Compliance | Multi-format citation audit |
| Abstract Bilingual | EN + 中文 abstracts |
| Peer Reviewer | 5-dimension review (max 2 rounds) |
| Formatter | LaTeX/DOCX/PDF output |
| **Socratic Mentor** | **Chapter-by-chapter guided planning (new in v2.0)** |

### Academic Paper Reviewer (v1.1)

7-agent multi-perspective review:

| Agent | Role |
|-------|------|
| Field Analyst | Identifies domain, configures reviewer personas |
| Editor-in-Chief | Journal fit, novelty, significance |
| Methodology Reviewer | Research design, statistics, reproducibility |
| Domain Reviewer | Literature coverage, theoretical framework |
| Perspective Reviewer | Cross-disciplinary, practical impact |
| **Devil's Advocate Reviewer** | **Core thesis challenge, logical fallacy detection, strongest counter-argument (new in v1.1)** |
| Editorial Synthesizer | Consensus analysis, revision roadmap |

**Modes:** full, re-review (verification), quick, methodology-focus, guided

### Academic Pipeline (v2.0)

9-stage orchestrator with integrity verification, two-stage review, and Socratic coaching:

| Stage | Skill | Purpose |
|-------|-------|---------|
| 1. RESEARCH | deep-research | Clarify RQ, find literature |
| 2. WRITE | academic-paper | Draft the paper |
| **2.5. INTEGRITY** | **integrity_verification_agent** | **100% reference & data verification** |
| 3. REVIEW | academic-paper-reviewer | 5-person review (EIC + R1/R2/R3 + Devil's Advocate) |
| → | *Socratic Revision Coaching* | *Guide user through review feedback* |
| 4. REVISE | academic-paper | Address review comments |
| 3'. RE-REVIEW | academic-paper-reviewer | Verification review of revisions |
| → | *Socratic Residual Coaching* | *Guide user through remaining issues (if Major)* |
| 4'. RE-REVISE | academic-paper | Final revision (if needed) |
| **4.5. FINAL INTEGRITY** | **integrity_verification_agent** | **100% final verification (zero issues required)** |
| 5. FINALIZE | academic-paper | MD + DOCX → ask LaTeX → confirm → PDF |

**Pipeline guarantees:**
- Every stage requires user confirmation checkpoint
- Integrity verification (Stage 2.5 + 4.5) cannot be skipped
- Reproducible — standardized process with full audit trail

---

## License

This work is licensed under [CC-BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).

**You are free to:**
- Share — copy and redistribute the material
- Adapt — remix, transform, and build upon the material

**Under the following terms:**
- **Attribution** — You must give appropriate credit
- **NonCommercial** — You may not use the material for commercial purposes

**Attribution format:**
```
Based on Academic Research Skills by Cheng-I Wu (HEEACT)
https://github.com/Imbad0202/academic-research-skills
```

---

## Author

**Cheng-I Wu** (吳政宜)
HEEACT — Higher Education Evaluation and Accreditation Council of Taiwan

---

## Changelog

### v2.0.1 (2026-03)
- **Simplify 4 SKILL.md** (-371 lines, -16.5%): remove cross-skill duplication, inline templates → file references, redundant routing tables, duplicate mode selection sections
- Fix revision loop cap contradiction between academic-paper and academic-pipeline

### v2.0 (2026-02)
- **academic-pipeline v2.0**: 5→9 stages, mandatory integrity verification, two-stage review, Socratic revision coaching, reproducibility guarantees
- **academic-paper-reviewer v1.1**: +Devil's Advocate Reviewer (7th agent), +re-review mode (verification), +post-review Socratic coaching
- New agent: `integrity_verification_agent` — 100% reference/data verification with audit trail
- New agent: `devils_advocate_reviewer_agent` — 8-dimension thesis challenger
- Output order: MD + DOCX → ask LaTeX → confirm → PDF

### v1.0 (2026-02)
- Initial release
- deep-research v2.0 (10 agents, 6 modes including socratic)
- academic-paper v2.0 (10 agents, 8 modes including plan)
- academic-paper-reviewer v1.0 (6 agents, 4 modes including guided)
- academic-pipeline v1.0 (orchestrator)
