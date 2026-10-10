# Anti-AI-Slop Skills

15 third-party skills to install. Source: "15 Free Skills That Kill AI Slop".

## Writing / response shape

| Skill | What it does | Kills | Install |
| --- | --- | --- | --- |
| `humanizer` | 35 named patterns, found and rewritten out. | "it's not just X, it's Y" and every em dash. | `npx skills add blader/humanizer` |
| `i-have-adhd` | Rebuilds the reply so the point lands in line one. | "Great question!" and the buried answer. | `npx skills add ayghri/i-have-adhd` |
| `stop-slop` | Hard bans on the way AI pads out a sentence. | Throat-clearing openers and every adverb. | `npx skills add hardikpandya/stop-slop` |
| `answer-first` | Ten rules that kill preamble on every reply. | The wind-up before the answer. | `npx skills add charlie947/answer-first` |
| `voiceprint` | Builds the piece from sentences you said out loud. | Words you never said. | `npx skills add charlie947/voiceprint` |

## UI / visual design

| Skill | What it does | Kills | Install |
| --- | --- | --- | --- |
| `ui-ux-pro-max-skill` | 79 UI styles and 119 UX rules it can search. | AI purple gradients and emoji as icons. | `npx skills add nextlevelbuilder/ui-ux-pro-max-skill` |
| `taste-skill` | Sets variance, motion and density per brief. | The centred, boilerplate layout. | `npx skills add Leonxlnx/taste-skill` |
| `impeccable` | A design language plus a 59-issue detector. | Inter everywhere and cards inside cards. | `npx skills add pbakaus/impeccable` |
| `hallmark` | Picks a structure, dresses it in one of 21 themes. | The default look every model learned. | `npx skills add Nutlope/hallmark` |
| `frontend-slides` | Shows you style options instead of asking for one. | Purple gradients on white. | `npx skills add zarazhangrui/frontend-slides` |

## Design tokens / diagrams

| Skill | What it does | Kills | Install |
| --- | --- | --- | --- |
| `design.md` | Brand tokens plus the reason each value exists. | The agent guessing your colours. | `npx skills add google-labs-code/design.md` |
| `awesome-design-md` | The same file, already written for 73 brands. | A blank design system. | `npx skills add VoltAgent/awesome-design-md` |
| `diagram-design` | 27 editorial diagram types in your own colours. | The generic rounded-box diagram. | `npx skills add cathrynlavery/diagram-design` |
| `archify` | Diagrams that trace back to real code. | Invented boxes nobody can check. | `npx skills add tt-a1i/archify` |
| `Understand-Anything` | Maps a codebase into a graph you click through. | A graph that shows off. | `npx skills add Egonex-AI/Understand-Anything` |

## Install status

Installed with `npx skills add` on 2026-10-10. Skills land in `.agents/skills/`
and are symlinked into `.claude/skills/`. Lockfile: `skills-lock.json`.

**13 of 15 repos installed, yielding 39 skills.** Several repos ship more than
one skill, so the count exceeds the roster.

| Repo | Skills installed |
| --- | --- |
| `blader/humanizer` | `humanizer` |
| `ayghri/i-have-adhd` | `i-have-adhd` |
| `hardikpandya/stop-slop` | `stop-slop` |
| `charlie947/answer-first` | `answer-first` |
| `charlie947/voiceprint` | `voiceprint` |
| `nextlevelbuilder/ui-ux-pro-max-skill` | 7: `ui-ux-pro-max`, `ui-styling`, `design`, `design-system`, `brand`, `banner-design`, `slides` |
| `Leonxlnx/taste-skill` | 13: `gpt-taste`, `brandkit`, `minimalist-ui`, `industrial-brutalist-ui`, `image-to-code`, `imagegen-frontend-web`, `imagegen-frontend-mobile`, `design-taste-frontend`, `design-taste-frontend-v1`, `stitch-design-taste`, `high-end-visual-design`, `redesign-existing-projects`, `full-output-enforcement` |
| `pbakaus/impeccable` | `impeccable` |
| `Nutlope/hallmark` | `hallmark` |
| `zarazhangrui/frontend-slides` | `frontend-slides` |
| `cathrynlavery/diagram-design` | `diagram-design` |
| `tt-a1i/archify` | `archify` |
| `Egonex-AI/Understand-Anything` | 9: `understand`, `understand-chat`, `understand-dashboard`, `understand-diff`, `understand-domain`, `understand-explain`, `understand-figma`, `understand-knowledge`, `understand-onboard` |

### The two that are not skills

`design.md` and `awesome-design-md` are a file format and a library of files
written in it. Neither installs as a skill.

- **`google-labs-code/design.md`** is a format spec plus a CLI and linter
  (`@google/design.md`): `lint` checks token references and WCAG contrast,
  `diff` catches regressions, `export` emits Tailwind or W3C DTCG JSON. The
  installer found that repo's own internal dev skills
  (`tdd-red-green-refactor`, `typed-service-contracts`), which have nothing to
  do with brand tokens and would trigger on unrelated TypeScript work. Both
  were removed. To use the format, write a `DESIGN.md` at the project root and
  lint it with the CLI.
- **`VoltAgent/awesome-design-md`** reported "No skills found", correctly: it is
  73 ready-made `DESIGN.md` files for brands like Stripe, Linear and Claude,
  each with `preview.html` and `preview-dark.html`. To use one, copy its
  `DESIGN.md` into the project root.

### Review before use

The installer's own warning: skills run with full agent permissions. These ship
executable code that a skill can invoke:

- `design-system/scripts/` — token validators, slide generation, background fetch (Python)
- `frontend-slides/scripts/` — `deploy.sh`, `export-pdf.sh`, `extract-pptx.py`
- `design/scripts/logo/` — logo search (Python)
- `brand/scripts/` — brand-to-token sync (Python)
- `understand-domain/extract-domain-context.py`
- `impeccable/scripts/data/font-index.json` — 1.1 MB font index

Nothing has run. No hooks were registered and `.claude/settings.json` holds only
the `npx skills` permission rule.

---

# Uploaded Archives

Five zip archives installed on 2026-10-10. They are five different kinds of
thing, so each took a different mechanism.

## Installed as skills (24)

Copied into `.agents/skills/` and symlinked into `.claude/skills/`, matching the
layout `npx skills` established. No name collided with the 39 already present.

| Archive | What it is | Skills |
| --- | --- | --- |
| `ai-second-brain` | A single skill: walks a non-technical user through the Obsidian + Karpathy-wiki setup from Charlie Hills's MarTech AI newsletter. | 1: `ai-second-brain` |
| `skills` (anthropics/skills) | Anthropic's own example-skill repository. The `skills/` folder only — `spec/` is the format spec and `template/` is a scaffold, neither a skill. | 19: `academy-guide`, `algorithmic-art`, `brand-guidelines`, `canvas-design`, `claude-api`, `discernment-nudge`, `doc-coauthoring`, `docx`, `frontend-design`, `internal-comms`, `mcp-builder`, `pdf`, `pptx`, `skill-creator`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing`, `xlsx` |
| `k12-teacher-skills` | The plugin shipped with Claude for Teachers, co-developed with Learning Commons. | 4: `k12-lesson-plan-creation`, `k12-lesson-differentiation`, `k12-lesson-prep`, `k12-check-for-understanding` |

Six of the anthropics/skills set — `docx`, `pdf`, `pptx`, `xlsx`,
`skill-creator`, `claude-api` — duplicate skills this session already loads from
the `anthropic-skills` plugin. The project copies carry no namespace prefix, so
both now appear in the listing and compete on the same triggers.

The k12 skills expect the Learning Commons Knowledge Graph connector for
standards lookups across all 50 states. Its `.mcp.json` also names nine
third-party education MCP servers (ASSISTments, Brisk Teaching, Canva, Coteach,
Diffit, Eedi, MagicSchool, Snorkl, TeachFX). **None were registered** — each is a
remote endpoint needing its own authorization. The skills degrade without the
connector; the repo says to adapt them.

## Installed as a project (9 skills)

`vendor/defending-code-reference-harness/` holds the whole repository, because
its skills drive its own Python code (`dnr_harness/`, `bin/`, `targets/`) and are
inert without it. The nine skills are symlinked into `.claude/skills/`:
`threat-model`, `vuln-scan`, `triage`, `patch`, `verify`, `quickstart`,
`customize`, `dnr-hunt`, `dnr-respond`. The repo's `.claude/skills/_lib/` is a
shared Python helper, not a skill, and is not linked.

**The harness does not run yet.** It needs
`python3 -m venv .venv && .venv/bin/pip install -e .` plus `flask` and `pyyaml`.
That was left undone — it installs and executes third-party code, which is the
user's call. Upstream states the repo is unmaintained and accepts no
contributions.

Five of its skills carry generic names — `verify`, `patch`, `triage`,
`customize`, `quickstart` — and will now compete for unrelated requests anywhere
in this project, not just inside the harness.

## Registered as a marketplace (0 plugins enabled)

`claude-plugins-official` is a plugin directory, not a skill pack, so it is
registered rather than copied into `.claude/skills/`. `vendor/claude-plugins-official/`
holds the repository and `.claude/settings.json` points `extraKnownMarketplaces`
at it.

Its manifest catalogues **315 plugins**; 54 are vendored in the archive (40
Anthropic-internal under `plugins/`, 14 third-party under `external_plugins/`)
and the rest resolve from GitHub or npm on install. Browse with `/plugin` and
install one with `/plugin install <name>@claude-plugins-official`.

**No plugin is enabled.** `enabledPlugins` is deliberately absent, so no MCP
server connects and no hook runs until something is installed by name. That
matters here: the external plugins include Discord, Telegram, iMessage, GitHub,
GitLab, Linear, Asana and Firebase integrations, each wanting its own
credentials. Anthropic's own README notes it does not control what those
plugins contain and cannot verify they will not change.

## Totals

72 skills in `.claude/skills/` — 39 from `npx skills`, 24 from these archives, 9
from the harness. One marketplace registered, no plugins enabled.
