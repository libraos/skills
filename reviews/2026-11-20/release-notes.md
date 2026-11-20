# Review: release-notes

| | |
|---|---|
| Skill name (frontmatter) | `release-notes` |
| Proposed catalogue id / group | `release-notes` / `sales-marketing` |
| Repository | https://github.com/phuryn/pm-skills |
| Path | `pm-execution/skills/release-notes` |
| Commit | `9af7bfd0bc47fdad43c2eaa7a43cd13918e7aaef` (exists; committed 2026-11-08) |
| Licence | MIT (repository-root `LICENSE`, "Copyright (c) 2026 Pawel Huryn") |
| Overall recommendation | **LIST** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There is one file, with no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 2569 | `148bf1cb1768` |

## Frontmatter

`name: release-notes` and `description:` (272 characters). There are no other keys.

## Checks

### 1. Credential access: PASS
Finding: none.

### 2. Network: PASS
Finding: "If they mention a product URL, use web search to understand the product and audience." (SKILL.md:14). This is conditional, triggered by the user, and fits the task. The Skill contains no URLs, fetch commands or connectors. JIRA and Linear are named only as kinds of export the user might supply (14).

### 3. Code: PASS
Finding: the folder has no non-markdown files and no commands. "Git logs" (SKILL.md:14) are an input the user provides. The Skill gives no `git` command.

### 4. Obfuscation: PASS
Finding: the file is valid UTF-8 with LF line endings and no byte-order mark. Its non-ASCII characters are U+2014 EM DASH (3 times) and U+00D7 MULTIPLICATION SIGN (once). There are no invisible, bidirectional or control characters, no HTML comments and no encoded runs.

### 5. Agent-steering: PASS
Finding: none. The Skill does not publish anywhere.

### 6. Reads and writes outside the task: PASS WITH NOTES
Finding: it reads files the user provides (SKILL.md:14). "Save as a markdown document. If the user wants HTML or another format, convert accordingly." (63) creates a new file without naming a location. That is expected for the task and nothing is destructive.

### 7. Promotion and third parties: PASS
Finding: none.

### 8. Content concerns: PASS WITH NOTES
Finding: the example user-facing line "Dashboards now load up to 3× faster" (SKILL.md:38) illustrates the tone. The Skill does not say that performance figures must come from the source material, so an agent could produce similar numbers on its own. Claims in the notes should be checked against the tickets.

### 9. Dangling references: PASS
Finding: there are no relative links.

### 10. Licence: PASS
Finding: the root `LICENSE` is MIT, "Copyright (c) 2026 Pawel Huryn". `pm-execution/.claude-plugin/plugin.json` gives `"license": "MIT"`. There is no NOTICE file and no `license:` frontmatter. There is no third-party content.
To install: copy the root `LICENSE`.

## Agent compatibility

`$ARGUMENTS` (SKILL.md:12) stays literal in Codex. Agents: claude, codex. This was not tested.

## Overall: LIST

The notes are that the Skill writes an output file and does not explicitly forbid invented metrics.

## What was read

Read in full: `SKILL.md`. For licence: the root `LICENSE` and `pm-execution/.claude-plugin/plugin.json`. Nothing was executed or followed.
