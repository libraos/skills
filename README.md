# AgentD Next Skills catalogue

`catalog.json` is the list of Skills that AgentD Next shows under **Recommended**, grouped by what they are for. `catalog.schema.json` describes its format.

The list is empty while the first entries are reviewed.

## What listing means

The Skills in `catalog.json` are third-party software. This repository contains catalogue entries, not third-party Skill files. Each entry identifies a source repository, a folder, a commit and the licence recorded for that version. When you choose Install, AgentD Next downloads that version from the source repository and copies it into the selected agents' Skills folders in the selected environment. The applicable upstream licence terms govern your rights in the Skill.

## How Skills are reviewed

Before listing, every file in the Skill's folder at the listed commit is read, by an automated agent and then by a person who signs the review off, looking for credential access, undeclared network calls, obfuscated code, and instructions to disable approvals or send data elsewhere. The review is recorded in the pull request that adds the entry.

The review covers the files in the listed folder at the specified commit. It does not cover external code or content those files may fetch, the services a Skill connects to, or later commits. This review can miss problems and does not guarantee safety.

We select Skills using the limited review described here. We do not test the quality of their results or guarantee their safety or suitability for your task. Each Skill's applicable licence sets out its terms, including any warranty disclaimers and liability limits. Nothing in this notice limits rights that cannot lawfully be excluded.

Third-party names identify the listed projects. Listing does not imply affiliation with or endorsement by their owners.

## Which Skills can be listed

A Skill can be listed only if the licences that apply to all of its installed files at the listed commit are approved by the Open Source Initiative. The entry records the main licence by SPDX identifier; the review records any separate component licences and required notices. Skills with no licence, or with a custom or source-available licence, are not listed.

## How an entry is added

An entry is added by pull request, using the template, and needs a code owner's approval. Each entry names the Skill's repository, its folder, and one full commit SHA. A newer commit is a new pull request.

## Removing an entry

Removing an entry removes it from subsequently fetched catalogues. Cached catalogues may still contain it. Removal from the catalogue does not delete or disable copies already installed.

Report security problems privately to contact@libraos.com. For licensing, attribution or rights-holder concerns, write to the same address.

## Licence

Except where otherwise stated, `catalog.json`, the schema and the templates are licensed under the MIT License. Linked Skills are subject to their own applicable licences.
