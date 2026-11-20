# Review: market-sizing

| | |
|---|---|
| Skill name (frontmatter) | `market-sizing` |
| Proposed catalogue id / group | `market-sizing` / `market-research` |
| Repository | https://github.com/phuryn/pm-skills |
| Path | `pm-market-research/skills/market-sizing` |
| Commit | `9af7bfd0bc47fdad43c2eaa7a43cd13918e7aaef` (exists; committed 2026-11-08) |
| Licence | MIT (repository-root `LICENSE`, "Copyright (c) 2026 Pawel Huryn") |
| Overall recommendation | **LIST** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There is one file, with no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 4424 | `58cc6c2de00e` |

## Frontmatter

`name: market-sizing` and `description:` (213 characters). There are no other keys.

## Checks

### 1. Credential access: PASS
Finding: none.

### 2. Network: PASS WITH NOTES
Finding: the Skill uses web search: "Use web search to find current market data, industry reports, and growth projections" (SKILL.md:18) and "Use web search for current industry data, analyst reports, and market benchmarks" (75). That fits the description. The only URLs are four "Further Reading" links to the author's site (87-90; see check 7). There are no fetch commands and no connectors.

### 3. Code: PASS
Finding: the folder has no non-markdown files. "customers × price × frequency" (SKILL.md:24) is a formula in prose, not code.

### 4. Obfuscation: PASS
Finding: the file is valid UTF-8 with LF line endings and no byte-order mark. Its non-ASCII characters are U+2014 EM DASH (2 times) and U+00D7 MULTIPLICATION SIGN (2 times). There are no invisible, bidirectional or control characters, no HTML comments and no encoded runs.

### 5. Agent-steering: PASS
Finding: none.

### 6. Reads and writes outside the task: PASS
Finding: it reads only files the user provides (SKILL.md:18). There are no writes.

### 7. Promotion and third parties: PASS WITH NOTES
Finding: there are four self-promotional links to the author's site, with no UTM or affiliate parameters:
- `https://www.productcompass.pm/p/market-research-advanced-techniques` (SKILL.md:87)
- `https://www.productcompass.pm/p/interviewing-customers-the-ultimate` (88)
- `https://www.productcompass.pm/p/crossing-the-chasm` (89)
- `https://www.productcompass.pm/p/product-innovation-masterclass` "(video course)" (90)
The "video course" may be a paid product; I did not check.

### 8. Content concerns: PASS WITH NOTES
Finding: the description lists "preparing for investor pitches". Market-size figures in a pitch can count as financial representations. The Skill's own safeguards are good: "Cite sources for market data — avoid unsupported numbers" (SKILL.md:76), "label estimates vs. data" (77) and "Confidence level for each" (68). Users should still check the figures independently before relying on them in fundraising material.

### 9. Dangling references: PASS
Finding: there are no relative links.

### 10. Licence: PASS
Finding: the root `LICENSE` is MIT, "Copyright (c) 2026 Pawel Huryn". There is no nearer licence file. `pm-market-research/.claude-plugin/plugin.json` gives `"license": "MIT"`. There is no NOTICE file and no `license:` frontmatter. "Crossing the Chasm" appears only as the title of a linked article; no book text is reproduced.
To install: copy the root `LICENSE`.

## Agent compatibility

`$ARGUMENTS` (SKILL.md:16) is Claude Code argument substitution and stays literal in Codex. Agents: claude, codex. This was not tested.

## Overall: LIST

The notes are the self-promotional links, including a possibly paid video course, and the fact that output may feed investor materials.

## What was read

Read in full: `SKILL.md`. For licence: the root `LICENSE` and `pm-market-research/.claude-plugin/plugin.json`. Not read: the linked pages. Nothing was executed or followed.
