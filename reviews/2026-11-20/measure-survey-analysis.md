# Review: survey-analysis (upstream name `measure-survey-analysis`)

> Listed under the upstream name `measure-survey-analysis`. The review below proposed a different id; the name mismatch it describes does not apply to the entry as listed.

| | |
|---|---|
| Skill name (frontmatter) | `measure-survey-analysis` |
| Proposed catalogue id / group | `survey-analysis` / `customer-research` |
| Repository | https://github.com/product-on-purpose/pm-skills |
| Path | `skills/measure-survey-analysis` |
| Commit | `3456e5e309f38ac2a66943f20d4aaf8031268dfb` (exists; committed 2026-11-14) |
| Licence | Apache-2.0 (repository-root `LICENSE`, "Copyright 2026 Jonathan Prisant"; frontmatter `license: Apache-2.0`) |
| Overall recommendation | **LIST WITH CAVEAT** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There are no hidden files, symlinks or submodules. The nested folders are `evals/` and `references/`.

| File | Bytes | Blob | What it is |
|---|---|---|---|
| `SKILL.md` | 12584 | `4aea3c0ccc5c` | Skill instructions |
| `HISTORY.md` | 4504 | `8e04f493183e` | Version history (prose) |
| `references/TEMPLATE.md` | 2602 | `c28ab9210a2c` | Output template |
| `references/EXAMPLE.md` | 7076 | `5615f528e5cf` | Worked example (all data marked fictional) |
| `evals/trigger-fixtures.json` | 3846 | `5419d8e26a88` | JSON test data: 18 sample queries with expected trigger/no-trigger |

## Frontmatter

`name: measure-survey-analysis`, `description:` (338 characters), `license: Apache-2.0`, and `metadata:` (`phase`, `version: "1.3.0"`, `updated`, `category`, `frameworks`, `author`). There is no `allowed-tools` key and there are no hooks or commands. SKILL.md:22 says "Read-only tools (Read, Grep); produces markdown output". That is a statement in prose and enforces nothing.

**Name mismatch:** the frontmatter `name` is `measure-survey-analysis` and the proposed id is `survey-analysis`. This is the same issue as for competitive-analysis-matrix: install under the upstream name or align the id.

## Checks

### 1. Credential access: PASS
Finding: none, in any of the five files.

### 2. Network: PASS
Finding: the Skill has no web-search, fetch or connector instructions. The only URLs are the attribution comment `https://github.com/product-on-purpose/pm-skills` (SKILL.md:13) and an issue link, `https://github.com/product-on-purpose/pm-skills/issues/253` (HISTORY.md:12), in prose.

### 3. Code: PASS
Finding: the only non-markdown file is `evals/trigger-fixtures.json`, which holds test data only (query, expected-result and notes fields). No file tells the agent to run it. There are no scripts, commands or installs.

### 4. Obfuscation: PASS
Finding: all five files are pure ASCII with LF line endings and no byte-order mark. There are no invisible or control characters and no encoded runs. There are seven HTML comments, all visible-intent text:
- SKILL.md:13, the attribution `<!-- PM-Skills | https://github.com/product-on-purpose/pm-skills | Apache 2.0 -->`.
- TEMPLATE.md:11, 16, 25, 32, 39, 52: authoring hints such as `<!-- Quotes drawn ONLY from provided excerpts, never invented. Mention counts are approximate. Flag clustering as AI-assisted. -->`.
Some lines are longer than 400 characters (SKILL.md:142, 150; HISTORY.md:7, 12, 20; EXAMPLE.md:15). They are ordinary prose and table rows.

### 5. Agent-steering: PASS
Finding: the "Refusal protocols" section (SKILL.md:138-152) is about refusing to *overstate statistical findings*. It does not tell the agent to refuse users in general or to override instructions. For example: "You refuse to overstate statistical significance from weak data." (140). Nothing about approvals, secrecy or persistence.

### 6. Reads and writes outside the task: PASS
Finding: it reads its own `references/TEMPLATE.md` and `references/EXAMPLE.md` (SKILL.md:198). There are no writes.

### 7. Promotion and third parties: PASS
Finding: none beyond the attribution comment.

### 8. Content concerns: PASS WITH NOTES
Finding: overall the Skill is notably careful: "Open-text quotes are drawn only from provided excerpts, never invented" (SKILL.md:207) and "No causal claim is made from cross-sectional data" (210). One borderline point is that a refusal template contains an unsourced, precise-sounding figure: "flag this finding as Biased (likely overstated by 20-40 percentage points based on instrument-bias research)" (SKILL.md:144). This cuts against the Skill's own rule against implied precision (205). An agent may repeat the "20-40 points" figure to users as if it were established. The example rule of thumb "+/- ~7% at n=200, 95%" (77) is arithmetically sound (about ±6.9%) and labelled approximate.

### 9. Dangling references: PASS WITH NOTES
Finding: these sibling Skills are named but not installed with this one: `discover-interview-synthesis`, `discover-journey-map`, `measure-experiment-design`, `measure-experiment-results`, `measure-okr-grader`, `define-prioritization-framework`, `define-problem-statement`, `define-hypothesis`, `deliver-prd`, `iterate-lessons-log` and `utility-pm-critic` (SKILL.md:23, 33-38, 191-194). The paths `library/skill-output-samples/measure-survey-analysis/`, `skills/discover-interview-synthesis/SKILL.md` and `skills/measure-experiment-results/SKILL.md` (216-218) are absent. HISTORY.md links `../../site/src/content/docs/releases/Release_v2.31.0.md`, `..._v2.30.0.md` and `..._v2.18.0.md` (18, 24, 37). The Skill handles one case explicitly: "If that skill is not available in the environment, say so rather than leaving a bare pointer" (150).

### 10. Licence: PASS
Finding: the same as competitive-analysis-matrix. The root `LICENSE` is Apache 2.0 with the boilerplate filled in as "Copyright 2026 Jonathan Prisant". There is no nearer licence file, the frontmatter has `license: Apache-2.0`, and both plugin manifests give `"license": "Apache-2.0"`. There is no NOTICE file in the repository and no third-party text or images.
To install: copy the root `LICENSE`. There is no NOTICE file.

## Agent compatibility

The repository ships a `.codex-plugin/plugin.json`. The Skill has no Claude-only syntax. Agents: claude, codex. This was not tested.

## Overall: LIST WITH CAVEAT

Caveat: the frontmatter name differs from the proposed id (see above). One unsourced "20-40 percentage points" bias figure (SKILL.md:144) may be repeated to users as fact. Many sibling-Skill pointers are absent when the Skill is installed alone.

## What was read

Read in full: all five files in the folder. For licence: the root `LICENSE`, `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json`. I also searched the repository tree for NOTICE or licence files. Nothing was executed or followed.
