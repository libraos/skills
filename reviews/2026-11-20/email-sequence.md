# Review: email-sequence

| | |
|---|---|
| Skill name (frontmatter) | `email-sequence` |
| Proposed catalogue id / group | `email-sequence` / `sales-marketing` |
| Repository | https://github.com/anthropics/knowledge-work-plugins |
| Path | `marketing/skills/email-sequence` |
| Commit | `0e0fcacddcc892eb92a1b7873ff9d68159c47571` (exists; committed 2026-11-19) |
| Licence | Apache-2.0 (`marketing/LICENSE`; also the root `LICENSE`) |
| Overall recommendation | **LIST** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There is one file, with no hidden files, nested folders, symlinks or submodules.

| File | Bytes | Blob |
|---|---|---|
| `SKILL.md` | 10627 | `32e4d65db0bd` |

## Frontmatter

`name: email-sequence`, `description:` (343 characters), `argument-hint: "[sequence type]"`. There is no `allowed-tools` key and there are no unusual keys.

## Checks

### 1. Credential access: PASS
Finding: none. "Personalization tokens" (SKILL.md:80) means mail-merge fields such as a first name, not credentials.

### 2. Network: PASS WITH NOTES
Finding: there are no URLs or fetch commands. The "Tool Integration" section (SKILL.md:146-165) covers the case where `~~email marketing` (Klaviyo, Mailchimp, Customer.io) or `~~marketing automation` / `~~CRM` (HubSpot, Marketo) is connected. There, the agent should "Reference how to set up the sequence as a flow" (149), "Reference lead scoring data to inform segmentation" (154) and "Use lifecycle stage data" (155). These are reads and advice. The Skill never tells the agent to create, activate or send a flow in a connected tool. With no tools connected, it delivers "copy-paste-ready format" (159). All of this fits the description, which is to design and draft sequences.

### 3. Code: PASS
Finding: the folder has no non-markdown files. The ASCII flow diagram (SKILL.md:182-198) is illustrative only.

### 4. Obfuscation: PASS
Finding: the file is valid UTF-8 with LF line endings and no byte-order mark. Its only non-ASCII character is U+2014 EM DASH (14 times). There are no invisible, bidirectional or control characters, no HTML comments and no encoded runs.

### 5. Agent-steering: PASS
Finding: the Skill has no send, schedule or activate step, and ends by asking the user (SKILL.md:215-220). It gathers inputs and asks "before proceeding" (19).

### 6. Reads and writes outside the task: PASS WITH NOTES
Finding: "Brand voice — if configured in local settings, apply automatically and inform the user" (SKILL.md:39). The local settings are not identified (the same note as for draft-content). There are no file writes and no destructive operations.

### 7. Promotion and third parties: PASS
Finding: Klaviyo, Mailchimp, Customer.io, HubSpot and Marketo appear only as examples of tool categories. There are no links.

### 8. Content concerns: PASS WITH NOTES
Finding: the suppression rules are responsible: "do not send if the recipient ... has unsubscribed from marketing" (SKILL.md:103). Two notes. First, the "Performance Benchmarks" table (109-114) gives figures such as an onboarding "Open rate | 50-70%" with no source. They are offered as targets, so they should be treated as rough. Second, the Skill never mentions consent or e-mail marketing law (for example CAN-SPAM, GDPR/PECR). The "Last chance with clear deadline" and "Limited-time offer" steps (129, 135) are standard, but the Skill does not warn against false urgency. Neither point is a breach of platform terms.

### 9. Dangling references: PASS WITH NOTES
Finding: `[CONNECTORS.md](../../CONNECTORS.md)` (SKILL.md:9) dangles. The `~~CRM` placeholder (153) is not defined even in the plugin's CONNECTORS.md, which covers `~~marketing automation` and `~~email marketing`. That is harmless.

### 10. Licence: PASS WITH NOTES
Finding: the same as the other `marketing/` Skills. `marketing/LICENSE` is clean Apache 2.0. The root `LICENSE` is Apache 2.0 with stray text appended by commit `d6c8015c2ff9`. There is no copyright line, no NOTICE file and no `license:` frontmatter, and the author is "Anthropic" per the manifest. There is no third-party content.
To install: copy `marketing/LICENSE`. There is no NOTICE file.

## Agent compatibility

`argument-hint`, "User runs `/email-sequence`" and the `~~` placeholders are Claude Code and plugin conventions, and they degrade gracefully. Agents: claude, codex. This was not tested.

## Overall: LIST

The notes are the unsourced benchmark figures and the absence of consent or legal-compliance guidance. The Skill drafts only and never sends.

## What was read

Read in full: `SKILL.md`. For licence and context: the root `LICENSE`, `marketing/LICENSE`, `marketing/.claude-plugin/plugin.json`, `marketing/CONNECTORS.md` and `marketing/.mcp.json`. Nothing was executed or followed.
