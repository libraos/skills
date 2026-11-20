# Review: competitive-brief

| | |
|---|---|
| Skill name (frontmatter) | `competitive-brief` |
| Proposed catalogue id / group | `competitive-brief` / `market-research` |
| Repository | https://github.com/anthropics/knowledge-work-plugins |
| Path | `marketing/skills/competitive-brief` |
| Commit | `0e0fcacddcc892eb92a1b7873ff9d68159c47571` (exists; committed 2026-11-19, "bump(datadog): 195f570c → a1603119 (#1420)") |
| Licence | Apache-2.0 (`marketing/LICENSE`; also the repository-root `LICENSE`) |
| Overall recommendation | **LIST WITH CAVEAT** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). The folder has one file. There are no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 13150 | `1a7df218996e` |

## Frontmatter

`name: competitive-brief`, `description:` (305 characters), `argument-hint: "<competitor or market segment>"`. There is no `allowed-tools` key, and there are no hooks, commands or other unusual keys.

## Checks

### 1. Credential access: PASS
Finding: no file reads keys, tokens, environment variables, `~/.ssh`, config or secret files, browser data or keychains.

### 2. Network: PASS WITH NOTES
Finding: there are no URLs and no curl/wget/fetch commands. The Skill tells the agent to use web search: "For each competitor, research using web search:" (SKILL.md:38). That matches the description ("Research competitors..."). It names services only as categories of source to consult: G2, Capterra, TrustRadius, Product Hunt (SKILL.md:60); Gartner, Forrester, IDC (61); TechCrunch (62); Reddit, Discourse, Slack communities (66). It also names "SEO tools" (64) and "Social listening" (63), but no specific product or MCP server. SKILL.md:9 points to the plugin's `CONNECTORS.md` for "unfamiliar placeholders". This Skill uses no `~~` placeholders itself. The plugin's `.mcp.json` sits outside the folder and is not installed with it, so installing this Skill configures no MCP server.

### 3. Code: PASS
Finding: the folder has no non-markdown files. There are no shell commands, scripts or package installs.

### 4. Obfuscation: PASS
Finding: the file is valid UTF-8 with LF line endings and no byte-order mark. Its only non-ASCII character is U+2014 EM DASH (11 times). There are no zero-width, bidirectional or control characters. There are no HTML comments, no base64-like or hex runs, and no lines longer than 400 characters.

### 5. Agent-steering: PASS WITH NOTES
Finding: nothing tells the agent to skip approvals, work silently, persist itself, change settings or memory, or send data anywhere. The Skill ends by asking the user what to do next (SKILL.md:325-331). It is borderline in one place. Among the sources to research it lists "**Product demos and free trials**: UX, features, onboarding experience" (SKILL.md:54). An agent with browser tools could read that as a reason to sign up for a competitor's trial, which means creating an account and accepting terms. The Skill does not require this, but it does not rule it out either. "Real-time alerts: ongoing (set up alerts for competitor brand mentions, press, job postings)" (SKILL.md:71) reads as advice for the human, not as an instruction to act.

### 6. Reads and writes outside the task: PASS
Finding: the Skill names no files to read or write, and contains no destructive operations.

### 7. Promotion and third parties: PASS
Finding: there are no links, affiliate or UTM parameters, or paid tools recommended by name. The review sites and analyst firms appear only as source categories.

### 8. Content concerns: PASS WITH NOTES
Finding: this is ordinary competitive-intelligence guidance. Two notes. First, it does not tell the agent to cite a source for each claim about a competitor. It only says "Note the date of the research" (SKILL.md:323). Output that criticises named companies should therefore be checked before it is shared. Second, see check 5 on free trials: signing up to a competitor's product to analyse it may breach that product's terms.

### 9. Dangling references: PASS WITH NOTES
Finding: `[CONNECTORS.md](../../CONNECTORS.md)` (SKILL.md:9) points outside the folder and will not resolve once the folder is copied on its own. The Skill works without it.

### 10. Licence: PASS WITH NOTES
Finding: the nearest licence is `marketing/LICENSE` (11,358 bytes), the unmodified Apache License 2.0 text. The repository-root `LICENSE` (11,607 bytes) holds the same text with ten lines of unrelated, non-legal text appended after the end of the licence. They were added by commit `d6c8015c2ff928e707a8119083d19be244a05215` ("Update LICENSE with syntax-file and code integration (#193)"), and begin "Syntax-file, code seperations,code vault integeted with css definition." The appended lines add no terms, but they mean the root file is no longer a clean copy of the licence. Neither file has a filled-in copyright line: the appendix placeholder `Copyright [yyyy] [name of copyright owner]` is left unchanged. The plugin manifest (`marketing/.claude-plugin/plugin.json`) gives the author as "Anthropic" and has no licence field. The SKILL.md frontmatter has no `license:` key. There is no NOTICE file anywhere in the repository at this commit. No file in the folder states a different licence or carries quoted third-party content.
To install: copy `marketing/LICENSE` alongside the Skill. There is no NOTICE file to carry.

## Agent compatibility

`argument-hint` and the trigger "User runs `/competitive-brief`" (SKILL.md:15) are Claude Code conventions. The same line also triggers on a plain request ("or asks for a competitive analysis..."), so Codex can use the Skill. Agents: claude, codex. This was not tested in either agent.

## Overall: LIST WITH CAVEAT

Caveat: the Skill does live web research on named companies. Its source list includes competitors' free trials, so users should not let the agent create accounts on third-party products, and should check claims about competitors before sharing them.

## What was read

Read in full: every file in the folder at the commit (`SKILL.md`). For licence and context only: the repository-root `LICENSE`, `marketing/LICENSE`, `marketing/.claude-plugin/plugin.json`, `marketing/CONNECTORS.md`, `marketing/.mcp.json`, and the history of the root `LICENSE`. Not read: any web page or service the Skill might lead an agent to, and other files in the repository. Nothing in the Skill was executed or followed.
