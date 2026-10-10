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

---

# Uploaded Archives, Round 2

Four archives installed on 2026-10-10. Again four different shapes.

## Installed as a skill (1)

| Archive | What it is |
| --- | --- |
| `unlazy` v2.1.0 | One skill whose `SKILL.md` sits at the repo root. Enforces completion discipline on long autonomous work: write acceptance gates first, decompose with a Depth Tree, run approved checks, re-verify evidence before reporting. Triggers include `/unlazy` and "do not stop until it is done". |

Installed to `.agents/skills/unlazy/` with its `agents/`, `references/`,
`research/`, `scripts/`, `templates/` and `tests/` intact; `.github/` dropped.

**It ships a Stop hook it wants installed.** `scripts/install-hooks.mjs` registers
`scripts/stop-hook.mjs`, which is what makes the gates block a turn from ending.
That was not run — a Stop hook changes how every turn in this project finishes.
Run it yourself if you want the enforcement, or use the skill without it and the
gates stay advisory. `.claude/settings.json` has no `hooks` block.

## Installed as a project (2 skills)

`vendor/launch-your-agent/` holds the whole repository, because its skills read
`cma-primitives.md`, `CLAUDE.md` and `ui/` (an example overview page, a build
sheet and a stylesheet) from the repo root. `launch-your-agent` and `wrap-up` are
symlinked into `.claude/skills/`.

An Anthropic reference implementation for building on Claude Managed Agents:
interview, scope a v0, launch it in your own account, grade it against your own
rubric, iterate, optionally put it on a schedule. Upstream states it is
unmaintained, accepts no contributions, and is deliberately token-intensive
because it explains each step.

## Registered as marketplaces (0 plugins enabled)

Both archives ship their own `.claude-plugin/marketplace.json` and their READMEs
say to install through Claude Code's plugin system, so both are registered
rather than copied into `.claude/skills/`.

| Marketplace | Plugins | What it is |
| --- | --- | --- |
| `skillx-marketplace` | 4 | SkillX.sh — a skills marketplace with a web app, a CLI and a hybrid search engine. Plugins: `skillx`, `skill-creator` v3.0.0, `marketing-mindset`, `hol-guard`. |
| `nextlevelbuilder-agentwiki` | 1 | `agentwiki` — drives the AgentWiki CLI (`@aiagentwiki/cli`) and its MCP server for documents, folders, search, knowledge-graph traversal, uploads and publishing. |

Registering rather than copying also resolved a collision: skillx ships its own
`skill-creator` v3.0.0, tuned for Skillmark benchmarks, which would have
overwritten the Anthropic `skill-creator` already in `.claude/skills/`. As a
plugin it stays namespaced, and both can coexist.

`vendor/skillx/` keeps the monorepo (`apps/`, `packages/`, `docs/`) but leaves
out ~9 MB of the maintainer's own database artifacts that shipped in the zip:
`scripts/seed-data.json`, `scripts/.content-update-progress.json` and the
`scripts/.tmp-update*.sql` files. None are needed to use the marketplace or the
skills. The `skillx` skill calls the published `npx skillx` package, not the
local checkout.

### Two things to know before enabling these

- The `skillx` skill's whole description is "Use this skill in every task", and
  its body shells out to `npx skillx`. Enabled, it would fire on every request
  and reach a network CLI each time.
- `agentwiki` talks to `https://api.agentwiki.cc/mcp` and an npm CLI, both
  needing their own credentials. No MCP server was registered.

`enabledPlugins` is still absent, so nothing from any of the three marketplaces
runs until you install it by name with
`/plugin install <name>@<marketplace>`.

## Totals

**75 skills** in `.claude/skills/`: 39 from `npx skills`, 24 from round-1
archives, 9 from the defending-code harness, 1 `unlazy`, 2 from
launch-your-agent. **Three marketplaces** registered (320 plugins catalogued),
none enabled. No hooks registered and no MCP servers added.

---

# Uploaded Archives, Round 3

Five archives installed on 2026-10-10. Four ship their own marketplace manifest
and are registered; one does not and is installed as a skill.

## Registered as marketplaces (0 plugins enabled)

| Marketplace | Plugins | What it is |
| --- | --- | --- |
| `exposure-audit` | 1 | Audits your own machine for live credentials left lying around and for things you switched off that are still on somewhere. Scopes the surface before scoring a twenty-item checklist, so items that cannot apply are marked NOT RUN rather than passed. Never prints a secret. Ships `validate-skills.sh`. |
| `skills-for-everyone` | 1 plugin, 7 skills | Charlie Hills's pack for people who use Claude daily but do not write code: `close`, `show-me`, `push-check`, `improve-system`, `workflow-maker`, `answer-first`, `prompt-lab`. Cut from 23 skills to seven. |
| `machiavelli` | 1 | Reads a business situation for power and leverage, then writes the message: one power-map table, ranked plays with costs, a paste-ready draft, and the move to avoid. |
| `charlie-free-mods` | 13 | Mod Maker plus 11 example mods and a virtual office: `mod-maker`, `safe-delete`, `secrets-guard`, `pre-build-check`, `mission-control`, `sessions-band`, `open-loops`, `outbox`, `plain-reply`, `done-ping`, `show-it`, `brand-theme`, `office`. |

Registering `skills-for-everyone` rather than copying it resolved a second
collision: it carries its own `answer-first` (78 lines) while the standalone
`charlie947/answer-first` already installed is a different, longer edition (116
lines). As a plugin the pack version stays namespaced and both survive.

`machiavelli` was read before installing. It is arm's-length negotiation
analysis, not manipulation tooling: it bans manufactured scarcity, invented
offers and fake urgency on the grounds that a called bluff costs more than the
deal, and it refuses to build a play against your own team, routing that to
management instead.

**`charlie-free-mods` is the one to be careful with.** Mods change Claude Code
itself — panes, status lines, guards before a command — and at least five of its
plugins (`plain-reply`, `open-loops`, `mission-control`, `secrets-guard`,
`brand-theme`) ship a `hooks/hooks.json`. Enabling one changes how every turn in
this project behaves. Its README also asks for Claude Code 2.1.287 or newer.

## Installed as a skill (1)

`agent-harness-starter` ships no marketplace manifest, so `vendor/agent-harness-starter/`
holds the repository and `agent-harness-setup` is symlinked into `.claude/skills/`.
It needs the repo: the skill reads `templates/CLAUDE.md`,
`templates/project-CLAUDE.md`, `templates/memory/`, `templates/agents/` and
`templates/skills/post-writer-example/` from the root, plus its own
`scripts/setup.sh` and `scripts/seed-claude-md.sh`.

An interactive scaffold for the six markdown components of an agent harness —
personalisation, context, action, memory and the rest — companion to Charlie
Hills's MarTech AI newsletter issue.

**Its `install.sh` was not run.** That script writes into `~/.claude/` globally:
it installs the skill and a slash command there, backing up and replacing
whatever it finds. That is a change to every project on the machine, not just
this one, so it is left for you. `templates/skills/post-writer-example/` is a
worked example for the scaffold, not a skill to install, and is not symlinked.

## Totals

**76 skills** in `.claude/skills/` and **seven marketplaces** registered
(336 plugins catalogued, none enabled). Still no hooks registered and no MCP
servers added.

### The skill listing is now over budget

At 76 skills the per-turn skill listing exceeds its context budget, so Claude
Code has begun truncating descriptions — a number of skills now appear by name
only, with no description, which is what they trigger on. Registering rounds 2
and 3 as marketplaces instead of copying their skills in kept roughly 25 more
skills out of the listing, but the 76 already there are over the line.

Two settings control it: `skillListingBudgetFraction` (default `0.01`, one
percent of the context window) and `skillListingMaxDescChars` (default `1536`).
Raising either costs context on every turn. The cheaper fix is fewer skills —
see the duplicate and generic-name problems recorded above.

---

# Uploaded Archives, Round 4

Five archives on 2026-10-10. Two were already installed, one registers as a
marketplace, two install as skills.

## Already installed — version check

| Archive | Result |
| --- | --- |
| `voiceprint` | **Byte-identical** to the installed copy. Nothing changed. |
| `impeccable` | Same version (4.5.2), but a **different build target**. Swapped. |

The impeccable repository builds one skill into roughly 24 agent-specific
directories — `.claude/`, `.cursor/`, `.gemini/`, `.grok/`, `.kiro/`, `.trae/`,
`.opencode/` and the rest — all from `skill/SKILL.src.md`. `npx skills`
installed the universal build, which spells its paths `.agents/skills/impeccable/`
and its commands `$impeccable`. The archive's `.claude/` build spells them
`.claude/skills/impeccable/` and `/impeccable`, and adds two frontmatter keys the
universal build omits: `user-invocable: true` and an `argument-hint` listing all
22 verbs. The Claude build is now installed, so `/impeccable` works as a real
slash command with argument completion.

The archive is 85 MB, almost all of it `tests/` (22 MB), `crates/` (14 MB of Rust
source) and those two dozen duplicate skill copies. Only the one Claude build was
taken.

## Registered as a marketplace

| Marketplace | Plugins | What it is |
| --- | --- | --- |
| `social-media-skills` | 1 plugin, 17 skills | `reels-scripting`, `hook-generator`, `post-writer`, `post-formatter`, `post-scorer`, `quote-post`, `pinned-comment`, `voice-builder`, `newsletter-voice`, `niche-research`, `content-matrix`, `profile-optimizer`, `graphic-designer`, `youtube-thumbnail`, `gemini-carousel`, `gemini-infographic`, `analytics-dashboard` |

## Installed as skills (26)

Neither pack ships a marketplace manifest, so both went into `.agents/skills/`
and are symlinked into `.claude/skills/`. No name collided.

**`life-automation-skills` — 13.** `company-setup` is the keystone: it interviews
once and writes a shared `company-profile.md` the other twelve read.
`inbox-executive-assistant`, `follow-up-chaser`, `invoice-chaser`,
`expense-wrangler`, `crm-hygiene`, `meeting-scheduler`, `meeting-notes`,
`standup-writer`, `weekly-review`, `task-capture`, `doc-drafter`,
`research-brief`. Most are read-and-propose only — they draft and the user sends,
and `crm-hygiene` shows merges as a change list before running them. They expect
Gmail or Microsoft 365, Google Calendar, and Airtable/Notion/HubSpot connectors.

**`motion-graphics-skills` — 13.** `brand-intake` is this pack's keystone: it
writes `brand.md` and `MOTION.md` plus a CLAUDE.md rule so the rest read your
colours, type and timing first. `motion-brief-writer`, `motion-effects`,
`animated-chart`, `milestone-reveal`, `launch-video`, `apple-launch-film`,
`title-sequence-3d`, `newsletter-promo`, `model-showdown`, `loop-cover`,
`reel-export`, `vox-explainer`. Its 13 MB `assets/` directory is entirely README
screenshots that no skill references, so `vendor/motion-graphics-skills/` keeps
only the README, prompts, licence and validator.

## Totals

**102 skills** and **eight marketplaces** (337 plugins catalogued, none enabled).
Still no hooks and no MCP servers.

## The skill listing is now badly over budget

This is no longer a warning. At 102 skills roughly **45 now appear with no
description at all** — among them `pdf`, `pptx`, `xlsx`, `skill-creator`,
`slides`, `stop-slop`, `unlazy`, `verify`, `patch`, `triage`, `quickstart`,
`ui-ux-pro-max`, `threat-model`, `vuln-scan`, every `understand-*`, and most of
the two packs just installed. A skill with no description in the listing cannot
be auto-selected; it only works if invoked by name. Nearly half the collection is
in that state.

Three ways out, in order of cost:

1. **Prune.** The six anthropics duplicates (`docx`, `pdf`, `pptx`, `xlsx`,
   `skill-creator`, `claude-api` — all still available as `anthropic-skills:*`)
   and the five generic harness names (`verify`, `patch`, `triage`, `customize`,
   `quickstart`) are 11 skills whose removal costs nothing. That alone gets back
   under 92.
2. **Repackage the two keystone packs as marketplaces.** They are the only two
   rounds installed as loose skills rather than plugins; moving them behind
   manifests takes 26 more out of the listing, leaving about 65.
3. **Raise the budget.** `skillListingBudgetFraction` (default `0.01`) and
   `skillListingMaxDescChars` (default `1536`) in `.claude/settings.json`. This
   keeps all 102 live and costs context on every single turn, in proportion.

---

# Uploaded Archives, Round 5

Four archives on 2026-10-10. Three register as marketplaces, one installs as a
skill — and two of the three replaced skills already installed loose.

## Registered as marketplaces

| Marketplace | Plugins | Skills behind them | What it is |
| --- | --- | --- | --- |
| `knowledge-work-plugins` | **123** | 252 | Plugins across 18 domains: `bio-research`, `customer-support`, `data`, `design`, `engineering`, `enterprise-search`, `finance`, `human-resources`, `legal`, `marketing`, `operations`, `product-management`, `productivity`, `sales`, `small-business`, `partner-built`, `pdf-viewer`, `cowork-plugin-management`. |
| `ui-ux-pro-max-skill` | 1 | 7 | The source repository of the pack `npx skills` installed in round 1. |
| `taste-skill` | 1 | 13 | The source repository of the pack `npx skills` installed in round 1. |

One `knowledge-work-plugins` entry, `noibu`, is not vendored: its source is a
`git-subdir` pinned to a SHA at `github.com/Noibu/ai-plugin.git`, fetched on
install. The other 122 resolve inside the vendored copy.

Both smaller manifests declare `source: "./"`, so the whole repository is the
plugin and each is vendored intact.

## 20 loose skills removed as superseded

`ui-ux-pro-max-skill` and `taste-skill` are the upstream repositories of 20
skills already sitting loose in `.agents/skills/`, installed by `npx skills` in
round 1. Their `SKILL.md` files are byte-identical to the installed copies, so
registering the marketplaces would have produced twenty exact duplicates — the
same skill both namespaced as a plugin and bare in the listing.

The loose copies were removed and the plugin form kept:

- From `ui-ux-pro-max-skill`: `ui-ux-pro-max`, `ui-styling`, `design`,
  `design-system`, `brand`, `banner-design`, `slides`.
- From `taste-skill`: `gpt-taste`, `brandkit`, `minimalist-ui`,
  `industrial-brutalist-ui`, `image-to-code`, `imagegen-frontend-web`,
  `imagegen-frontend-mobile`, `design-taste-frontend`, `design-taste-frontend-v1`,
  `stitch-design-taste`, `high-end-visual-design`, `redesign-existing-projects`,
  `full-output-enforcement`.

Nothing was lost. Every one is still installable by name from its marketplace,
and both archives are vendored in full.

## Installed as a skill (1)

`remove-ai-design-slop` ships no manifest, so it went into `.agents/skills/`.
Builds the four files (a `REFERENCE.md`, a `DESIGN.md` and four lines in
`CLAUDE.md`) that make later graphics come out on brand, checks work against 29
tells, and turns a long list into a graphic that reads as a reference document
rather than an AI card grid. Its frontmatter states it targets the free tier at
claude.ai — no paid plan, API key or install.

## Totals

**83 skills** (down from 102) and **eleven marketplaces** holding **462
plugins**, none enabled. Still no hooks and no MCP servers. The repository is
about 142 MB, 67 MB of it under `vendor/`.

### Listing pressure, eased but not fixed

This round removed 19 skills net from the listing — the first reduction in the
project — by taking the plugin form of two packs instead of keeping both forms.
Descriptions should return for some skills that had lost them.

83 is still above where the listing fits comfortably. The two cheapest remaining
cuts, both still outstanding:

1. The six skills duplicating the `anthropic-skills` plugin: `docx`, `pdf`,
   `pptx`, `xlsx`, `skill-creator`, `claude-api`.
2. The five generically named harness skills that fire on unrelated requests:
   `verify`, `patch`, `triage`, `customize`, `quickstart`.

Taking both gets to 72. Repackaging `life-automation-skills` and
`motion-graphics-skills` as marketplaces, as every other multi-skill pack now
is, would reach roughly 46.
