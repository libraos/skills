# Review: copywriting

| | |
|---|---|
| Skill name (frontmatter) | `copywriting` |
| Proposed catalogue id / group | `copywriting` / `sales-marketing` |
| Repository | https://github.com/coreyhaines31/marketingskills |
| Path | `skills/copywriting` |
| Commit | `5b2b400eec1e7e1cec76245a715d0b0d4fd2a9c1` (exists; committed 2026-11-20, "Merge pull request #1019 from coreyhaines31/integrate/vendor-guides-batch") |
| Licence | MIT (repository-root `LICENSE`, "Copyright (c) 2025 Corey Haines"). It credits ideas adapted from a separate MIT-licensed project (see check 10). |
| Overall recommendation | **LIST WITH CAVEAT** |

## File inventory

The listing comes from the git tree API at the commit (recursive, not truncated). There are no hidden files, symlinks or submodules. The nested folders are `evals/` and `references/`.

| File | Bytes | Blob | What it is |
|---|---|---|---|
| `SKILL.md` | 15238 | `d70d0b8855f2` | Skill instructions |
| `references/ai-tells.md` | 20804 | `0a93ab3b88fc` | Style blacklist and self-check |
| `references/copy-frameworks.md` | 14409 | `c19bc984e6f6` | Headline formulas and page templates |
| `references/natural-transitions.md` | 5561 | `5fba31a5d3bf` | Phrase list |
| `evals/evals.json` | 12995 | `f903d8b9db5b` | JSON test data: 10 prompts with expected outputs and assertions |

## Frontmatter

`name: copywriting`, `description:` (478 characters), and `metadata: version: 2.3.6`. There is no `allowed-tools` key and there are no hooks or commands.

## Checks

### 1. Credential access: PASS
Finding: none, in any of the five files.

### 2. Network: PASS
Finding: the Skill has no web-search, fetch or connector instructions. All URLs are citations or pointers that the agent is not told to open:
- `https://github.com/retieedra-profound/skills-marketing-library` (SKILL.md:77; ai-tells.md:306): attribution for adapted ideas, an MIT-licensed repository owned by "Profound".
- `https://github.com/zstvns/design-skills` (SKILL.md:341): "If the designskills library is installed, hand off the visual work". This is a third-party MIT-licensed repository and there is no install instruction.
- ai-tells.md:299-307 (Sources): `https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing`, `https://arxiv.org/abs/2406.07016`, `https://aclanthology.org/2025.coling-main.426/`, `https://arxiv.org/abs/2510.15061`, `https://eqbench.com/slop-score.html`, `https://tropes.fyi/tropes-md`, `https://www.ignorance.ai/p/the-field-guide-to-ai-slop`, `https://www.blakestockton.com/p/dont-write-like-ai-1-101-negation`, `https://robotsatemyhomework.substack.com/p/ai-writing-patterns`.

### 3. Code: PASS
Finding: the only non-markdown file is `evals/evals.json`, which holds test prompts, expected outputs and assertions. Nothing tells the agent to run it, and it contains no code or URLs. There are no scripts, commands or installs.

### 4. Obfuscation: PASS WITH NOTES
Finding: all files are valid UTF-8 with LF line endings and no byte-order mark. There are no zero-width, bidirectional, control or private-use characters, no HTML comments and no base64 or hex runs. These visible non-ASCII characters appear:
- SKILL.md: U+2192 arrow (×6), U+2014 em dash (×2), U+274C ❌ (×1), U+2705 ✅ (×1).
- ai-tells.md: ✗ U+2717 (×6), ✓ U+2713 (×5), → (×5), U+2013 en dash (×4), em dash (×2), 🚀 U+1F680, ✨ U+2728, ✅, × U+00D7, and four MATHEMATICAL SANS-SERIF BOLD letters (U+1D5EF, U+1D5FC, U+1D5F9, U+1D5F1) spelling "𝗯𝗼𝗹𝗱". The bold letters are a deliberate example on line 217: "**Unicode decoration** (Ban): arrows, ×, 𝗯𝗼𝗹𝗱 letters in body copy." They are not hidden text.
- copy-frameworks.md: … (×10), ✅ (×4), 🚩 (×4), → (×2), U+2212 minus (×2), ×.
- evals.json: em dash (×4).
The long lines (SKILL.md:3, the description; evals.json, prompt strings) are ordinary text.

### 5. Agent-steering: PASS
Finding: there are no instructions about approvals, secrecy, persistence, settings or sending data. Three phrases look like steering but are not:
- "don't silently drop it" (SKILL.md:103) is the opposite of hiding.
- "Before a full rewrite of Situation A copy ... answer these silently:" (ai-tells.md:241) means working out the writer persona internally before drafting. It is not about hiding actions.
- "**Rules that override the persona:**" (ai-tells.md:259) means the anti-fabrication rules override the imagined writer persona. It is not about overriding the system or the user.

### 6. Reads and writes outside the task: PASS WITH NOTES
Finding: "If `.agents/product-marketing.md` exists (or `.claude/product-marketing.md`, or the legacy `product-marketing-context.md` filename, in older setups), read it before asking questions." (SKILL.md:15), and "Check its **Learnings** section before drafting" (16). These are reads of the user's own project context files. One of them is inside a `.claude/` directory. No writes or destructive operations are instructed. Users should know the Skill looks for these files.

### 7. Promotion and third parties: PASS WITH NOTES
Finding:
- The author cites his own book: "Figures cited in Corey Haines's *Founding Marketing* (Ch. 3) associate clearer positioning and copy with: +81% conversions, −38% sales cycle, −28% CAC, +175% referrals" (copy-frameworks.md:423-428), with the same figures at SKILL.md:84. No underlying study is cited.
- It names other skills from the same library: copy-editing, cro, emails, popups, ab-testing (SKILL.md:132, 335-339), offers (description).
- A third-party library is named for hand-off (SKILL.md:341).
- Real brands appear as headline examples: Ahrefs (copy-frameworks.md:54), Drip (71), Amazon (38) and Slack (SKILL.md:170). SavvyCal is a case study (copy-frameworks.md:407-419).
There are no affiliate or UTM parameters, and no paid tool is recommended for the user to buy.

### 8. Content concerns: PASS WITH NOTES
Finding: the anti-fabrication rules are strong: "no invented stats, customers, or results" (SKILL.md:48); "Fabricated statistics or testimonials erode trust and create legal liability" (121); "Never invent experience ... a fake customer quote" (ai-tells.md:260); "Don't invent to de-slop" (272). Notes:
- Unsourced performance claims about named third parties may be repeated as fact: "That one line roughly tripled (3×) conversions" for SavvyCal (copy-frameworks.md:413), and the book-cited percentages above.
- The stated purpose of the "No AI Tells" section is to make AI-drafted copy read as human-written ("Clients and buyers reject copy that reads as AI-written", SKILL.md:138; "Human-sounding copy", ai-tells.md:241). This is style guidance. It never tells the agent to hide that a draft was AI-assisted from the user, or to evade platform detection. Some publishers and platforms do require AI disclosure, and users remain responsible for meeting it.

### 9. Dangling references: PASS WITH NOTES
Finding: all relative links resolve inside the folder (`references/copy-frameworks.md`, `references/ai-tells.md`, `references/natural-transitions.md`). These sibling Skills are named but not installed with this one: copy-editing, cro, emails, popups, ab-testing, offers, and seo-audit (`references/ai-writing-detection.md`, ai-tells.md:309).

### 10. Licence: PASS WITH NOTES
Finding: the root `LICENSE` is the standard MIT text, "Copyright (c) 2025 Corey Haines". There is no nearer licence file. `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json` give `"license": "MIT"` and the author "Corey Haines". There is no NOTICE file in the repository and no `license:` frontmatter.
Third-party content: "Diagnosis, the three-question gate, and decompose-and-lock adapted from Profound's `improved-copywriting` skill ([skills-marketing-library](...), MIT), re-expressed for this skill." (SKILL.md:77). Also: "Profound's `humanizer` and `improved-copywriting` skills and Wispr Flow's `writing` skill ... (MIT): the build-a-writer questions, human-writing traits, and second-generation tells" (ai-tells.md:306). That repository is MIT-licensed, "Copyright (c) 2026 Profound".

I compared those three upstream files at their current default branch, not a pinned commit, using shared 8-word sequences. Verbatim overlap is about 1.3% of SKILL.md tokens and 0.6% of ai-tells.md, in short phrases such as "the best fix its worst flaw and lock it". That supports the "re-expressed" description: the ideas are adapted, not copied. On that basis Profound's copyright notice is probably not required, but a cautious installer could include it. The Wikipedia guide and the papers are cited as sources "rewritten in our own words" (ai-tells.md:297); I did not compare against them. natural-transitions.md:5 says "Adapted from: University of Manchester Academic Phrasebank (2023), Plain English Campaign". The phrases are short, common transitions, but the Phrasebank is a copyrighted resource and I did not compare against it.
To install: copy the root `LICENSE`. Optionally, also carry the Profound MIT notice as a courtesy.

## Agent compatibility

The repository ships a `.codex-plugin/plugin.json`. The Skill has no `$ARGUMENTS` or slash-command syntax. The `.claude/product-marketing.md` path is one of three alternatives. Agents: claude, codex. This was not tested.

## Overall: LIST WITH CAVEAT

Caveat: (1) it reads the user's `.agents/` or `.claude/product-marketing.md` context file if present. (2) It carries the author's own unsourced book statistics and a third-party "3× conversions" claim, which an agent could repeat to clients. (3) It credits adapted MIT material from another project. The overlap check suggests the material was re-expressed, but the signer should record the attribution.

## What was read

Read in full: all five files in the folder. For licence and context: the root `LICENSE`, `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`, the licence section of `README.md`, and the `LICENSE` of `retieedra-profound/skills-marketing-library`. For the overlap measurement only: `profound/humanizer/SKILL.md`, `profound/improved-copywriting/SKILL.md` and `wisprflow/writing/SKILL.md` from that repository. Not read: the cited web pages and papers, and the Academic Phrasebank. Nothing was executed or followed.
