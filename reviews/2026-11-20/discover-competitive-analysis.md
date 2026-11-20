# Review: competitive-analysis-matrix (upstream name `discover-competitive-analysis`)

> Listed under the upstream name `discover-competitive-analysis`. The review below proposed a different id; the name mismatch it describes does not apply to the entry as listed.

| | |
|---|---|
| Skill name (frontmatter) | `discover-competitive-analysis` |
| Proposed catalogue id / group | `competitive-analysis-matrix` / `market-research` |
| Repository | https://github.com/product-on-purpose/pm-skills |
| Path | `skills/discover-competitive-analysis` |
| Commit | `3456e5e309f38ac2a66943f20d4aaf8031268dfb` (exists; committed 2026-11-14) |
| Licence | Apache-2.0 (repository-root `LICENSE`, "Copyright 2026 Jonathan Prisant"; frontmatter `license: Apache-2.0`) |
| Overall recommendation | **LIST WITH CAVEAT** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There are no hidden files, symlinks or submodules. The nested folders are `evals/`, `evals/output-scenarios/` and `references/`.

| File | Bytes | Blob | What it is |
|---|---|---|---|
| `SKILL.md` | 4550 | `c1d301b3a64f` | Skill instructions |
| `HISTORY.md` | 2883 | `884c17e731e2` | Version history (prose) |
| `references/TEMPLATE.md` | 5401 | `72b9b57e1d44` | Output template |
| `references/EXAMPLE.md` | 10823 | `9f6376872a40` | Worked example |
| `evals/trigger-fixtures.json` | 4253 | `f45288cabc1a` | JSON test data: sample user queries with expected trigger/no-trigger |
| `evals/output-scenarios/notetaking-market.md` | 2318 | `69129325387b` | Eval input brief (prose) |

## Frontmatter

`name: discover-competitive-analysis`, `description:` (354 characters), `license: Apache-2.0`, and `metadata:` (`phase`, `version: "2.2.1"`, `updated`, `category`, `frameworks`, `author: product-on-purpose`). There is no `allowed-tools` key and there are no hooks or commands.

**Name mismatch:** the frontmatter `name` is `discover-competitive-analysis`, but the proposed catalogue id is `competitive-analysis-matrix`. Under the Agent Skills convention, `name` should match the folder name. If the installer copies the Skill into a folder called `competitive-analysis-matrix`, agents that check this, or that use the folder name, may show a different name or warn. Recommend either installing into a folder named `discover-competitive-analysis` or making the catalogue id match.

## Checks

### 1. Credential access: PASS
Finding: none, in any of the six files.

### 2. Network: PASS WITH NOTES
Finding: "Research each competitor through public sources: websites, pricing pages, G2/Capterra reviews, press releases, job postings, and customer testimonials." (SKILL.md:42) means web research, which fits the description. It names no tool and no URL to fetch. The only URL in SKILL.md is inside an HTML comment, an attribution line: `<!-- PM-Skills | https://github.com/product-on-purpose/pm-skills | Apache 2.0 -->` (SKILL.md:13). There are no connectors or MCP servers.

### 3. Code: PASS
Finding: the only non-markdown file is `evals/trigger-fixtures.json`. It holds plain test data (`"q"`, `"expect"`, `"split"`, `"notes"` and `"near_miss_of"` fields for 20 sample queries). Nothing in the Skill tells an agent to run or read it. It contains no code, commands or URLs. There are no scripts or package installs anywhere in the folder.

### 4. Obfuscation: PASS
Finding: all six files are pure ASCII with LF line endings and no byte-order mark. There are no invisible or control characters and no base64 or hex runs. There are nine HTML comments, and every one is visible-intent text:
- SKILL.md:13, the attribution comment quoted above.
- TEMPLATE.md:19, 39, 63, 166, 177, 182, 187, 192: section hints such as `<!-- Rate as: Full, Partial, None, Unknown -->` and `<!-- Competitive developments to monitor -->`.
None of them carries instructions to the agent beyond filling in the template. One line is longer than 400 characters: HISTORY.md:6, an ordinary table row.

### 5. Agent-steering: PASS
Finding: none. "Avoid dismissing competitors. Respect drives better strategy." (SKILL.md:51) and "Be honest about uncertainty." (57) push toward caution.

### 6. Reads and writes outside the task: PASS
Finding: it reads only its own `references/TEMPLATE.md` and `references/EXAMPLE.md` (SKILL.md:61, 77). There are no writes.

### 7. Promotion and third parties: PASS
Finding: there is no self-promotion beyond the attribution comment. Real companies appear in the example and evals: Asana, Monday.com, ClickUp, Notion (EXAMPLE.md:34-37), and Otter.ai, Fireflies.ai, Gong, Granola, Zoom AI Companion (notetaking-market.md:25-34). There are no links, UTM tags or affiliate tags.

### 8. Content concerns: PASS WITH NOTES
Finding: EXAMPLE.md makes statements about real, named companies. Nearly every factual claim is tagged `[fictional]`, for example "Occasional performance and reliability issues [fictional]" for ClickUp (EXAMPLE.md:149). A few lines are not tagged. "New entrants from BI space moving into PM (e.g., if Tableau/Looker launched PM features)" (205) is hypothetical. The "Sources and Confidence" table lists "Gartner, IDC reports 2025" and "Product websites, free trials" (EXAMPLE.md:211-215) without a `[fictional]` tag, which models citing sources that were never consulted. The risk is low because the file is plainly an example. The instructions themselves tell the agent to "Note what you can verify vs. what you're inferring" (SKILL.md:42).

### 9. Dangling references: PASS WITH NOTES
Finding: these sibling Skills are named but not installed with this one: `discover-market-sizing`, `foundation-lean-canvas`, `tool-foundation-sprint-differentiation`, `define-jtbd-canvas` and `define-problem-statement` (SKILL.md:3, 29-32). HISTORY.md has links that leave the folder: `../../site/src/content/docs/releases/Release_v2.32.0.md` (HISTORY.md:12) and `../../site/src/content/docs/releases/Release_v2.30.0.md` (23). The Skill works without them.

### 10. Licence: PASS
Finding: the root `LICENSE` is Apache License 2.0. The appendix instructions have been removed and the boilerplate filled in as "Copyright 2026 Jonathan Prisant". The terms are otherwise identical to the standard text, word for word. There is no nearer licence file. The frontmatter has `license: Apache-2.0`, the HTML comment says "Apache 2.0", and `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json` both give `"license": "Apache-2.0"` and the author "product-on-purpose". There is no NOTICE file anywhere in the repository. The frontmatter `frameworks: [triple-diamond, lean-startup, design-thinking]` names methods only. There is no quoted third-party text and there are no images.
To install: copy the root `LICENSE`. There is no NOTICE file.

## Agent compatibility

The repository ships a `.codex-plugin/plugin.json`, so the author targets Codex as well as Claude Code. The Skill uses no `$ARGUMENTS`, slash commands or `~~` placeholders. Agents: claude, codex. This was not tested.

## Overall: LIST WITH CAVEAT

Caveat: the frontmatter name (`discover-competitive-analysis`) differs from the proposed id. Install the Skill under its own name, or align the id, so agents do not report a mismatch. The worked example contains untagged "sources" next to fictional claims about real companies.

## What was read

Read in full: all six files in the folder. For licence: the root `LICENSE` (diffed against the standard Apache 2.0 text), `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json`. I also searched the repository tree for NOTICE or other licence files and found none. Nothing was executed or followed.
