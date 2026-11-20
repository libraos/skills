# Review: summarize-interview

| | |
|---|---|
| Skill name (frontmatter) | `summarize-interview` |
| Proposed catalogue id / group | `summarize-interview` / `customer-research` |
| Repository | https://github.com/phuryn/pm-skills |
| Path | `pm-product-discovery/skills/summarize-interview` |
| Commit | `9af7bfd0bc47fdad43c2eaa7a43cd13918e7aaef` (exists; committed 2026-11-08) |
| Licence | MIT (repository-root `LICENSE`, "Copyright (c) 2026 Pawel Huryn") |
| Overall recommendation | **LIST WITH CAVEAT** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There is one file, with no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 2036 | `b4fee4359979` |

## Frontmatter

`name: summarize-interview` and `description:` (244 characters). There are no other keys.

## Checks

### 1. Credential access: PASS
Finding: none.

### 2. Network: PASS
Finding: there is no web search, fetch or connector use. The only URLs are two "Further Reading" links to the author's site (SKILL.md:52-53).

### 3. Code: PASS
Finding: the folder has no non-markdown files and no commands.

### 4. Obfuscation: PASS
Finding: the file is valid UTF-8 with LF line endings and no byte-order mark. Its non-ASCII characters are U+2014 EM DASH (3 times) and U+0142 LATIN SMALL LETTER L WITH STROKE (once, in the author's name "Paweł" in the example on line 43). There are no invisible, bidirectional or control characters, no HTML comments and no encoded runs.

### 5. Agent-steering: PASS
Finding: none.

### 6. Reads and writes outside the task: PASS WITH NOTES
Finding: "Read any attached files first" (SKILL.md:14) refers to the user's transcript. "Save the summary as a markdown document in the user's workspace." (SKILL.md:46) makes the agent write a new file without asking for a name or location. That fits the task and nothing is overwritten or deleted, but users should know a file will be created. The template asks for "**Participants**: [Full names and roles]" (28). The saved summary will therefore hold personal data about interviewees, and the Skill gives no guidance on consent, redaction or storage.

### 7. Promotion and third parties: PASS WITH NOTES
Finding: there are self-promotional links with no UTM or affiliate parameters:
- `https://www.productcompass.pm/p/interviewing-customers-the-ultimate` (SKILL.md:52)
- `https://www.productcompass.pm/p/cpdm` "Continuous Product Discovery Masterclass (CPDM) (video course)" (53)
The example action item uses the author's name: `"2025-01-15, Paweł Huryn, Follow up with customer about pricing"` (43).

### 8. Content concerns: PASS
Finding: the Skill makes no claims. "a primary school graduate should be able to understand the summary" (SKILL.md:22) is a style instruction.

### 9. Dangling references: PASS
Finding: there are no relative links.

### 10. Licence: PASS
Finding: the root `LICENSE` is MIT, "Copyright (c) 2026 Pawel Huryn". There is no nearer licence file. `pm-product-discovery/.claude-plugin/plugin.json` gives `"license": "MIT"`. There is no NOTICE file and no `license:` frontmatter. "Jobs to Be Done" is named as a method only.
To install: copy the root `LICENSE`.

## Agent compatibility

`$ARGUMENTS` (SKILL.md:12) stays literal in Codex. Agents: claude, codex. This was not tested.

## Overall: LIST WITH CAVEAT

Caveat: the Skill processes interview transcripts containing personal data. It asks for participants' full names and saves the summary as a new file in the user's workspace without asking where.

## What was read

Read in full: `SKILL.md`. For licence: the root `LICENSE` and `pm-product-discovery/.claude-plugin/plugin.json`. Not read: the linked pages. Nothing was executed or followed.
