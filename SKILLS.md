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
