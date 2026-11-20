# Review: user-personas

| | |
|---|---|
| Skill name (frontmatter) | `user-personas` |
| Proposed catalogue id / group | `user-personas` / `customer-research` |
| Repository | https://github.com/phuryn/pm-skills |
| Path | `pm-market-research/skills/user-personas` |
| Commit | `9af7bfd0bc47fdad43c2eaa7a43cd13918e7aaef` (exists; committed 2026-11-08) |
| Licence | MIT (repository-root `LICENSE`, "Copyright (c) 2026 Pawel Huryn") |
| Overall recommendation | **LIST** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There is one file, with no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 3047 | `dd486a376020` |

## Frontmatter

`name: user-personas` and `description:` (236 characters). There are no other keys.

## Checks

### 1. Credential access: PASS
Finding: none.

### 2. Network: PASS
Finding: there is no web search, fetch or connector use. The only URLs are three "Further Reading" links (SKILL.md:67-69).

### 3. Code: PASS
Finding: the folder has no non-markdown files. "read and analyze them directly using available tools" (SKILL.md:18) refers to the user's own CSV or Excel files. It names no command.

### 4. Obfuscation: PASS
Finding: the file is valid UTF-8 with LF line endings and no byte-order mark. Its only non-ASCII character is U+2014 EM DASH (once). There are no invisible, bidirectional or control characters, no HTML comments and no encoded runs.

### 5. Agent-steering: PASS
Finding: none.

### 6. Reads and writes outside the task: PASS
Finding: it reads only research files the user provides. There are no writes.

### 7. Promotion and third parties: PASS WITH NOTES
Finding: there are self-promotional links with no UTM or affiliate parameters:
- `https://www.productcompass.pm/p/interviewing-customers-the-ultimate` (SKILL.md:67)
- `https://www.productcompass.pm/p/market-research-advanced-techniques` (68)
- `https://www.productcompass.pm/p/jobs-to-be-done-masterclass-with` "Jobs-to-be-Done Masterclass with Tony Ulwick and Sabeen Sattar (video course)" (69). This names third parties as course presenters.

### 8. Content concerns: PASS
Finding: "Ground all insights in actual data; avoid assumptions" (SKILL.md:57) and "Flag any data gaps" (61). The Skill has no problematic claims.

### 9. Dangling references: PASS
Finding: there are no relative links.

### 10. Licence: PASS
Finding: the root `LICENSE` is MIT, "Copyright (c) 2026 Pawel Huryn". `pm-market-research/.claude-plugin/plugin.json` gives `"license": "MIT"`. There is no NOTICE file and no `license:` frontmatter. There is no third-party text.
To install: copy the root `LICENSE`.

## Agent compatibility

`$ARGUMENTS` (SKILL.md:16, 52) stays literal in Codex. Agents: claude, codex. This was not tested.

## Overall: LIST

The only note is the self-promotional reading links.

## What was read

Read in full: `SKILL.md`. For licence: the root `LICENSE` and `pm-market-research/.claude-plugin/plugin.json`. Nothing was executed or followed.
