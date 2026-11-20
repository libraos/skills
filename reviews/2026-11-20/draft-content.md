# Review: draft-content

| | |
|---|---|
| Skill name (frontmatter) | `draft-content` |
| Proposed catalogue id / group | `draft-content` / `sales-marketing` |
| Repository | https://github.com/anthropics/knowledge-work-plugins |
| Path | `marketing/skills/draft-content` |
| Commit | `0e0fcacddcc892eb92a1b7873ff9d68159c47571` (exists; committed 2026-11-19) |
| Licence | Apache-2.0 (`marketing/LICENSE`; also the root `LICENSE`) |
| Overall recommendation | **LIST** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There is one file, with no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 4612 | `39de3a17733c` |

## Frontmatter

`name: draft-content`, `description:` (323 characters), `argument-hint: "<content type and topic>"`. There is no `allowed-tools` key and there are no unusual keys.

## Checks

### 1. Credential access: PASS
Finding: none.

### 2. Network: PASS
Finding: there are no URLs, fetch commands, web-search instructions or connector use. The social platforms it names (LinkedIn, Twitter/X, Instagram, Facebook, SKILL.md:23 and 61-63) are formatting targets only. Nothing is posted.

### 3. Code: PASS
Finding: the folder has no non-markdown files and no commands.

### 4. Obfuscation: PASS
Finding: the file is valid UTF-8 with LF line endings and no byte-order mark. Its only non-ASCII character is U+2014 EM DASH (6 times). There are no invisible, bidirectional or control characters, no HTML comments and no encoded runs.

### 5. Agent-steering: PASS
Finding: the Skill produces drafts and ends by asking: "Would you like me to revise any section..." (SKILL.md:117). It contains no publish, send or post step.

### 6. Reads and writes outside the task: PASS WITH NOTES
Finding: "If the user has a brand voice configured in their local settings file, apply it automatically. Inform the user that brand voice settings are being applied." (SKILL.md:41). The "local settings file" is never identified. In the original plugin this is plugin configuration. Installed on its own, an agent may go looking for a file to match, or simply ask. The instruction is benign: it is a read, and it tells the agent to inform the user. It is just vague. There are no writes and no destructive operations.

### 7. Promotion and third parties: PASS
Finding: none.

### 8. Content concerns: PASS WITH NOTES
Finding: the Skill uses placeholders for proof rather than inventing it: "Social proof placeholder" (SKILL.md:78), "Supporting quotes (provide placeholder guidance)" (87), "Results section with metrics (prompt user for data)" (97). It reminds the user to include an unsubscribe note in newsletters (72). However, it also asks for "Introduction with a hook (question, statistic, bold statement, or story)" (49) and "data references in each section" (51) without saying that statistics must be real and sourced. Drafts should be checked for invented figures.

### 9. Dangling references: PASS WITH NOTES
Finding: `[CONNECTORS.md](../../CONNECTORS.md)` (SKILL.md:9) dangles. The Skill uses no placeholders, so nothing is lost.

### 10. Licence: PASS WITH NOTES
Finding: the same position as the other `marketing/` Skills. `marketing/LICENSE` is the unmodified Apache 2.0 text. The root `LICENSE` is Apache 2.0 with stray non-legal text appended by commit `d6c8015c2ff9`. There is no filled-in copyright line, no NOTICE file anywhere in the repository and no `license:` frontmatter. The manifest gives the author as "Anthropic". There is no third-party content.
To install: copy `marketing/LICENSE`. There is no NOTICE file.

## Agent compatibility

`argument-hint` and "User runs `/draft-content`" (SKILL.md:15) are Claude Code conventions. The natural-language trigger on the same line works anywhere. Agents: claude, codex. This was not tested.

## Overall: LIST

There are minor notes only: the unidentified "local settings file", the lack of an explicit rule against invented statistics, and the dangling link.

## What was read

Read in full: `SKILL.md`. For licence only: the root `LICENSE`, `marketing/LICENSE` and `marketing/.claude-plugin/plugin.json`. Nothing was executed or followed.
