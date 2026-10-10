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

None installed yet. The session's permission classifier denies both `npx skills add`
and read-only `git clone` of these repos, so no skill files have been fetched.

### Verified from the repo listings

All five writing repos exist and are public. Layouts differ:

- `blader/humanizer` — `SKILL.md` at root. v3.1.0, MIT. Markdown only.
- `hardikpandya/stop-slop` — `SKILL.md` at root plus `references/`. MIT. Markdown only.
- `charlie947/answer-first` — `skills/answer-first/`, `.claude-plugin/`. Markdown only.
- `ayghri/i-have-adhd` — ships `hooks/`, `scripts/`, `extensions/`, `package.json`. **Executable code.**
- `charlie947/voiceprint` — ships `bin/`, `setup.sh`, `trace.py`. **Executable code.**

The ten design repos have not been inspected.

### Review before installing

`i-have-adhd` installs hooks that run on tool calls, and `voiceprint` has a shell
setup script. Read both before letting either run.
