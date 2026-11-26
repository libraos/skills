# Review: film-production

| | |
|---|---|
| Skill name (frontmatter) | `film-production` |
| Proposed catalogue id / group | `film-production` / `video-production` (new group, "Video and film production") |
| Repository | https://github.com/libraos/film-factory |
| Path | `skills/film-production` |
| Commit | `cf5cfde478d9b03cbf3d4f131533fd590ace1f93` (exists; committed 2026-11-25 20:06:19 UTC, "Harden film.py: keep the key on the configured host, https by default, paths inside the project; append to existing AGENTS.md") |
| Licence | MIT (repository-root `LICENSE`, "Copyright (c) 2026 LibraOS") |
| Overall recommendation | **LIST WITH CAVEAT** |

The Skill's author, LibraOS, also publishes this catalogue. The review applies the same checks as to a third-party Skill, but the reader should know the reviewer and the author are not independent.

## File inventory

The listing comes from `git ls-tree -r -l` at the commit, in a fresh clone. There are no hidden files, symlinks or submodules in the folder. The nested folders are `assets/`, `assets/project/`, `assets/project/film/`, `scripts/` and `tests/`.

| File | Bytes | Blob | What it is |
|---|---|---|---|
| `SKILL.md` | 4764 | `596931608e27` | Skill instructions |
| `assets/env.example` | 600 | `5b335c90310d` | Settings template, copied to `~/.config/film-kit/env` |
| `assets/project/AGENTS.md` | 3651 | `a973230805d6` | Worker rules, copied into the user's project as `AGENTS.md` and `CLAUDE.md` |
| `assets/project/film/brief.md` | 108 | `99d16d34e176` | Placeholder brief |
| `assets/project/gitignore` | 33 | `4bec8bde9914` | Copied into the project as `.gitignore` |
| `scripts/film.py` | 23944 | `0e2b1e842ab6` | Python 3 script (standard library only), copied into the project as `tools/film.py`: all model calls, ffmpeg and Chrome |
| `tests/test_film.py` | 8086 | `e681d3e07350` | unittest suite for `film.py` (redirects, URL rules, path rules, one ffmpeg build test) |

## Frontmatter

`name: film-production` and `description:` (387 characters). There is no `allowed-tools` key, no `license:` key and there are no hooks or slash commands.

## Checks

### 1. Credential access: PASS WITH NOTES
Finding: the script needs a bearer key for the image and video endpoints and gets it three ways (film.py:57-69): `FILM_VIDEO_KEY` / `FILM_IMAGE_KEY` as a plain value, `_KEY_FILE` (any path the user configures, read with `open(...).read()`, film.py:63), or `_KEY_CMD`, **a command string run through a shell** (`subprocess.run(conf(p + "_CMD"), shell=True, ...)`, film.py:65) whose stdout is taken as the key. Settings are read from `$FILM_ENV` (default `~/.config/film-kit/env`, film.py:33) and then overridden by every `FILM_*` environment variable (film.py:44). Whoever can write that file or set `FILM_*` variables for the process can make `film.py` run an arbitrary shell command each time it needs a key, which is every `doctor`, `keyframe` and `render`, including runs by workers.
The key is sent as `Authorization: Bearer` only to the configured base URL (film.py:153); `SafeRedirect` removes the header when a redirect changes scheme, host or port (film.py:131-145), and image result URLs are fetched without it (film.py:191). The key is not printed: error messages carry the method, path and up to 300 characters of the response body, not the request headers (film.py:164-166). The instructions keep the key out of the repository ("Never commit a key", env.example:1; "never print, copy or commit a key", AGENTS.md:5). `FILM_ALLOW_HTTP=1` (film.py:111) lets the key travel unencrypted to a non-loopback host; it is off by default and documented as such (SKILL.md:71).

### 2. Network: PASS WITH NOTES
Finding: the script makes HTTP calls to endpoints the user configures, and to URLs those endpoints return:
- `FILM_IMAGE_BASE_URL`: `POST /images/generations` with the prompt (film.py:249), `POST /images/edits` with the prompt and a keyframe image from the project (film.py:246-247), `GET /models` (film.py:484).
- `FILM_VIDEO_BASE_URL`: `POST /videos` with the shot prompt and the first and last keyframe images (film.py:307-309), `GET /videos/ID` polled every 15 s for up to 2 hours (film.py:28, 313-324), `GET /videos/ID/content` (film.py:330), `GET /models` (film.py:484).
- Any `https://` URL (or loopback `http://`) that the image endpoint returns as `data[0].url` is downloaded without the key, with a 120 s timeout and a 64 MiB cap (film.py:185-208, 256). The endpoint therefore chooses a host the script will contact.
Base URLs must be `https://`, or `http://` on loopback, unless `FILM_ALLOW_HTTP=1` (film.py:105-123); other schemes (`file://`, `ftp://`) are refused, also on redirect (film.py:136-138). The default in env.example:2-3 is `https://gateway.libraos.com/v1` for both. Prompts and keyframes leave the machine for those endpoints; the README says so (README.md:28). There is no other network use: no web search, no fetch instruction for the agent.
SKILL.md:47-48 tells the user that Codex workers need network and that the owner turns it on with `libraos-core config set dispatch.codex_network true`. That widens what every Codex worker on that host can reach, not only this Skill's.

### 3. Code: PASS WITH NOTES
Finding: `scripts/film.py` is real code that the agent copies into the user's project and runs (SKILL.md:17-23; AGENTS.md:3). Exactly what it executes:
- A shell command from settings, `FILM_*_KEY_CMD`, with `shell=True` and a 60 s timeout (film.py:65). This is the only shell use.
- `ffmpeg` (from `FILM_FFMPEG` or `PATH`, film.py:81-85) as an argument list, no shell, for cropping keyframes, conforming clip length, contact sheets, encoding, concatenation (`-f concat -safe 0` on a list file the script writes, film.py:389-394) and reading durations (film.py:257, 275, 289, 375, 385, 394, 398, 427).
- Chrome or Chromium headless (from `FILM_CHROME`, `google-chrome` or `chromium`, film.py:345) on a local `file://` HTML page it writes for each title card, with a temporary profile; the card text is HTML-escaped (film.py:348). When run as root it adds `--no-sandbox` (film.py:353-354), so a root run renders without Chrome's sandbox.
- `tests/test_film.py` runs ffmpeg when executed; nothing tells the agent to run it.
There are no installs, no downloads of code and no `eval`/`exec`. I did not run the script or its tests.

### 4. Obfuscation: PASS
Finding: all seven files are valid UTF-8 with LF line endings and no byte-order mark, and contain only ASCII characters. There are no zero-width, bidirectional or control characters, no HTML comments and no base64 or hex runs. The longest line is SKILL.md:3, the description (400 characters including the key).

### 5. Agent-steering: PASS WITH NOTES
Finding: there are no instructions about secrecy, approvals of tool permissions or sending data elsewhere. Notes:
- The Skill writes standing agent instructions into the user's repository: `assets/project/AGENTS.md` is copied to both `AGENTS.md` and `CLAUDE.md`, or appended to existing ones (SKILL.md:18-21). From then on every Claude or Codex session in that repository reads "They describe the film in plain words and expect you to run the stages below without being told how" and the hand-off rules (AGENTS.md:9-13). This is persistence beyond the Skill's own invocation; it is scoped to the film project, but in a repository that is not only a film project it would steer unrelated sessions.
- "Never ask the person for stage names, budgets, commands or file names" (SKILL.md:9-10; AGENTS.md:13) tells the agent to choose budgets itself (30 minutes for planning, 15 + 6 or 15 + 25 minutes per shot, SKILL.md:26, 34-35). These are time budgets for workers; the image and video calls cost money on the user's endpoints and the Skill gives no spending limit.
- The approval step is in favour of the user: "Stop here. Do not render." (SKILL.md:30); "Work stops after stage 1 until a person says the keyframes are approved" (AGENTS.md:17). But "When the person agrees, in whatever words" (SKILL.md:33) leaves it to the agent to read consent.

### 6. Reads and writes outside the task: PASS WITH NOTES
Finding:
- Writes into the user's repository without a separate confirmation: `tools/film.py`, `AGENTS.md`, `CLAUDE.md`, `.gitignore` (appended to if present, SKILL.md:17-21), `film/brief.md`, and then commits ("Commit.", SKILL.md:22; AGENTS.md:29, 44). Stage 2 commits clips, contact sheets and `out/film.mp4` (AGENTS.md:44), so large binary media go into git history.
- Asks the user to create `~/.config/film-kit/env` and a key file outside the repository (SKILL.md:45; env.example:1, 4).
- Reads files outside the project by design: the settings file, the key file, and `FILM_MUSIC_DIR` (listed, and one track copied into `film/`, film.py:407-423; the name must match a listed file, so there is no path traversal there).
- The script checks that keyframe, reference, shot and music paths stay inside the project, resolving symlinks (film.py:215-229, 241-242, 299, 398). **The `sheet` subcommand skips that check**: `film.py sheet CLIP OUT` passes both paths through `rel()` only (film.py:498), so an absolute or `../` path reads and writes outside the project, contrary to the docstring's "Paths must stay inside the project" (film.py:20). The Skill's own flow never calls `sheet` directly, only through `render` and `build` with fixed paths.
- Title cards write a temporary HTML file next to the card image in `out/work/` and delete it (film.py:349-357).

### 7. Promotion and third parties: PASS WITH NOTES
Finding: the Skill is built around the author's own products: "LibraOS Engine workers" (SKILL.md:3, 25, 33; AGENTS.md:10), "the key is the one from LibraOS Next" (SKILL.md:46), the `libraos-core` command (SKILL.md:48) and the default gateway `https://gateway.libraos.com/v1` (env.example:2-3). It works with any OpenAI-shaped `/v1/images` and `/v1/videos` endpoint, and stage work falls back to the agent itself when no worker can be started (SKILL.md:27, 36-37). env.example:5-6 names specific third-party models as defaults (`minimax-h3`, `gpt-image-2.6`). There are no affiliate or tracking parameters.

### 8. Content concerns: PASS WITH NOTES
Finding: the picture rules forbid "likeness of a real person" and "brand names or logos in the picture" (AGENTS.md:53), and "Nothing in the picture that the brief did not ask for" (AGENTS.md:52). Notes:
- There is no guidance on labelling the result as AI-generated. Some platforms and jurisdictions require disclosure of synthetic video; that stays the user's responsibility.
- Music comes from "instrumental scores the team may use" (SKILL.md:69); the Skill does not check rights, so licensing of the score is the user's.
- The agent is told to say what it could not check: "what only a person can judge: motion, pacing and sound" (SKILL.md:38-39; AGENTS.md:61-62). That is accurate: the checks (film.py:436-477) test that files exist, the shot count, prompt length, durations and that the film ends on a card, not what the picture shows.

### 9. Dangling references: PASS WITH NOTES
Finding: all paths inside the folder resolve (`scripts/film.py`, `assets/project/AGENTS.md`, `assets/project/gitignore`, `assets/env.example`). Not shipped with the Skill and not defined in it:
- "LibraOS Engine workers" and how to hand a stage to one (SKILL.md:25, 33). Without them the agent does the stage itself, which the Skill allows.
- `libraos-core` (SKILL.md:48), a LibraOS command.
- The "team gateway" and "LibraOS Next" key (SKILL.md:46).
- External programs: Python 3, `ffmpeg`, Chrome or Chromium (SKILL.md:49).
- `assets/project/film/brief.md` is in the folder but step 1 does not list it among the files to copy; the agent writes `film/brief.md` from the user's words instead (SKILL.md:21-22). Harmless.

### 10. Licence: PASS
Finding: the root `LICENSE` is the standard MIT text, "Copyright (c) 2026 LibraOS". There is no nearer licence file, no NOTICE file and no `license:` frontmatter; README.md:37-39 says "MIT. See LICENSE." No third-party code or text is credited or apparent: the script imports only the Python standard library (film.py:22-23). The `examples/` folders at the repository root are outside the Skill and were not reviewed.
To install: copy the root `LICENSE`.

## Agent compatibility

The Skill writes the same rules to `AGENTS.md` (Codex, others) and `CLAUDE.md` (Claude Code), and SKILL.md:47-48 addresses Codex workers' network explicitly. There is no `$ARGUMENTS` or slash-command syntax and no `allowed-tools`. Both agents need permission to run `python3`, `ffmpeg` and Chrome, and network for the endpoints; Codex workers have no network by default and cannot render until the owner turns it on. Agents: claude, codex. This was not tested.

## Overall: LIST WITH CAVEAT

Caveat: (1) it copies a script into the user's project and runs it; the script sends prompts and keyframes to endpoints the user configures, downloads image results from URLs those endpoints return, runs ffmpeg and headless Chrome (without its sandbox when run as root), and **runs a user-configured key command through a shell** (`FILM_*_KEY_CMD`). (2) It writes `AGENTS.md`, `CLAUDE.md`, `.gitignore` and `tools/film.py` into the repository and commits, including rendered media; the `AGENTS.md`/`CLAUDE.md` rules keep steering later sessions in that repository. (3) It sets its own time budgets and gives no spending limit for paid image and video calls. (4) The `sheet` subcommand does not apply the inside-the-project path check the rest of the script applies. (5) It is built around LibraOS services (workers, gateway, `libraos-core`), works with any OpenAI-shaped endpoint, and is published by the same organisation as this catalogue.

## What was read

Read in full: all seven files in the folder at the commit, from a fresh clone. For licence and context: the root `LICENSE`, `README.md` and `.gitignore`, and the commit's metadata. Not read: `examples/pier-nine` and `examples/tidal-city`. Nothing was executed: not `film.py`, not the tests, and no endpoint was contacted.
