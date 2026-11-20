# Review: competitor-analysis

| | |
|---|---|
| Skill name (frontmatter) | `competitor-analysis` |
| Proposed catalogue id / group | `competitor-analysis` / `market-research` |
| Repository | https://github.com/phuryn/pm-skills |
| Path | `pm-market-research/skills/competitor-analysis` |
| Commit | `9af7bfd0bc47fdad43c2eaa7a43cd13918e7aaef` (exists; committed 2026-11-08, "v2.3.0: live-qa, live-polls, survey-design") |
| Licence | MIT (repository-root `LICENSE`, "Copyright (c) 2026 Pawel Huryn") |
| Overall recommendation | **LIST** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There is one file, with no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 4814 | `b9cafee194fc` |

## Frontmatter

`name: competitor-analysis` and `description:` (258 characters). There are no other keys.

## Checks

### 1. Credential access: PASS
Finding: none.

### 2. Network: PASS WITH NOTES
Finding: the Skill uses web search: "Conduct web research to identify direct competitors" (SKILL.md:18), "Use web search to identify 5 primary direct competitors" (23), "Use web search to identify product launches, funding, executive moves" (96). That fits the description. The only URLs are two "Further Reading" links to the author's own site (SKILL.md:109-110; see check 7). The agent is not told to fetch them. No MCP server or connector is used.

### 3. Code: PASS
Finding: the folder has no non-markdown files and no commands.

### 4. Obfuscation: PASS
Finding: the file is pure ASCII with LF line endings and no byte-order mark. There are no invisible or control characters, no HTML comments and no encoded runs.

### 5. Agent-steering: PASS
Finding: the persona line "You are a strategic product analyst..." (SKILL.md:13) is the only framing. There are no instructions about approvals, secrecy, persistence or acting outside the request.

### 6. Reads and writes outside the task: PASS
Finding: it reads only files the user provides ("If the user provides market research ... read and analyze them directly", SKILL.md:18). There are no writes.

### 7. Promotion and third parties: PASS WITH NOTES
Finding: the "Further Reading" section links to the author's newsletter site, with no UTM or affiliate parameters:
- `https://www.productcompass.pm/p/market-research-advanced-techniques` (SKILL.md:109)
- `https://www.productcompass.pm/p/interviewing-customers-the-ultimate` (SKILL.md:110)
These are self-promotional but plainly labelled. Some of the site's content may be paywalled; I did not check.

### 8. Content concerns: PASS WITH NOTES
Finding: the guidance is mainstream, including "Validate competitive insights across multiple sources" (SKILL.md:98). It asks for "Estimated market share" and "Customer satisfaction and retention signals" (40, 48, 56), which are often not public. Unless the agent says that such figures are estimates, they risk being presented as fact. The Skill does not tell the agent to cite sources.

### 9. Dangling references: PASS
Finding: there are no relative links.

### 10. Licence: PASS
Finding: the root `LICENSE` at the commit is the standard MIT text, "Copyright (c) 2026 Pawel Huryn". There is no nearer licence file. The plugin manifest `pm-market-research/.claude-plugin/plugin.json` gives `"license": "MIT"` and the author "Paweł Huryn". There is no `license:` frontmatter and no NOTICE file in the repository. There is no third-party content.
To install: copy the root `LICENSE` (the copyright notice and permission notice) alongside the Skill.

## Agent compatibility

`$ARGUMENTS` (SKILL.md:16, 22, 26, 72, 77, 87) is Claude Code argument substitution. In Codex it will stay as literal text, and the agent has to infer the product from the user's message, which it normally can. Agents: claude, codex. This was not tested.

## Overall: LIST

The notes are the self-promotional reading links and unsourced market-share estimates.

## What was read

Read in full: `SKILL.md`. For licence: the root `LICENSE`, `pm-market-research/.claude-plugin/plugin.json` and the licence section of the root `README.md`. Not read: the linked web pages. Nothing was executed or followed.
