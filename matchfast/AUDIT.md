# MatchFast homepage: design and frontend audit

Audited 11 Oct 2026 against the live site and a full-page capture.

## Design Read

Reading this as: **redesign-preserve** of a B2B technology discovery platform for
technical and commercial buyers, with a dark data-credibility language, leaning
toward native CSS tokens plus DM Sans and Inter with restrained scroll motion.

Dials, read off the existing site rather than taken from baseline:
`DESIGN_VARIANCE 6` (currently ~5, grid-regular), `MOTION_INTENSITY 3`
(currently ~2, almost static), `VISUAL_DENSITY 7` (currently ~7, a dense
directory and correctly so).

## Stack, as measured

| Layer | Finding |
| --- | --- |
| CMS | WordPress 7.1.3 |
| Page builder | Elementor 4.3.2 |
| Theme | ThinkRank 2.9.0 |
| Server | PHP 8.5.11, `hcdn` |
| Other | Site Kit by Google 1.189.0, REST API exposed at `/wp-json/` |

Elementor widgets actually used on the homepage: `icon-list` x5, `heading` x5,
`spacer` x4, `text-editor` x3, `html` x3, `divider` x1. Most of the distinctive
sections are custom markup inside `html` widgets rather than native Elementor
components, which matters: a CSS layer can restyle most of this page without
touching Elementor structure.

**The codebase is not in this repository.** No theme, no templates, no
`wp-content`. Everything below is derived from the rendered site. Implementation
notes say where each change would land, but applying them needs either the repo
or a WordPress developer.

## Information architecture, as it exists

Fifteen homepage sections, in order: hero and project search; trending rankings;
featured directories; category and industry coverage; how it works; software
rankings; company rankings by city and service; editorial opinion pieces; a
second statistics band; company leaderboard; project-fit matcher; verification;
recently updated; ranking methodology and FAQ; footer.

This IA is sound. It moves from intent capture to proof to depth, and it should
be preserved. The problems are in hierarchy, rhythm and repetition, not in order.

## The ten weaknesses that matter

**1. The hero carries nine competing elements.** Badge pill, H1, subtext, search
field, "Start with your idea" line, a category strip, two text links, and a
four-number statistics band, all above the fold. The discipline limit is four.
Everything after the search field dilutes the one action the hero exists to
produce.

**2. Eyebrow labels on almost every section.** `TRENDING THIS WEEK`,
`FEATURED DIRECTORIES`, `HOW IT WORKS`, `SOFTWARE`, `TOP RANKED LISTICLES`,
`OPINION PIECES`, `LEADERBOARD`, `PROJECT FIT`, `VERIFICATION`, `EDITORIALS`,
`METHOD`. Eleven across fifteen sections. The ceiling is one per three, so five.
The uniform label-then-headline rhythm is the single strongest templated tell on
the page.

**3. One section inverts the page theme.** "Company rankings by city and
service" is a pale band inside an otherwise dark page. A reader scrolling past
it feels they have landed on a different site. A theme switch is allowed once as
a deliberate device; this reads as an accident.

**4. Two statistics bands with unrelated numbers.** The hero shows 640 / 25,778 /
384 / 169. A later band shows 3 / 167 / 56 / 263. Eight numbers, no stated
relationship, and the second set is weaker than the first. One band, the
strongest four figures, placed once.

**5. Section numbering used as decoration.** `01 / 02 / 03` on the how-it-works
cards and `01` to `05` down the software list. The content is already ordered by
position. Numbering it twice adds chrome, not information, and reads as AI
default.

**6. The leaderboard uses filled progress tracks.** Five rows, each with a bar on
a filled background track, all showing 5.0. A bar whose value never varies
carries no information and is the classic "meter with no quantity behind it".
The rating number alone is stronger.

**7. Repeating card-grid layout families.** Trending rankings, company rankings,
and opinion pieces are three horizontal card rows with image-or-text, title,
meta. Three sections sharing one layout family across a fifteen-section page
flattens the whole scroll. At least four distinct families are needed.

**8. Five overlapping calls to action.** "Post a Project", "AI Company Finder",
"List Your Company", "Share a project brief", "Try the matcher". At least three
of those are the same buyer intent expressed three ways, which splits attention
and makes measurement meaningless.

**9. Almost no motion, on a page that needs sequencing.** The page is effectively
static. With fifteen sections and high density, nothing guides the eye between
blocks. This is the cheapest available improvement: entry reveals at section
level, nothing more.

**10. Two separate dense lists rendered as hairline rows.** "Recently updated"
and the leaderboard both use a row-per-item list with a rule under every row.
Over five items this is the weakest available layout, and it appears twice.

## What is working and must be kept

- **The evidence-first editorial voice.** "Firms that fail are named on the page,
  not hidden." "Placement cannot be bought." "A 4.8 from forty reviewers
  outranks a 5.0 from three." This is the product's real differentiator and it
  is rare. Do not touch the copy.
- **Dating every figure.** "Verified 15 Sep 2026", "Checked 11 September 2026".
  Most directories hide recency. Showing it is a credibility asset.
- **The white search field against the dark page.** The single highest-contrast
  object on the screen is the primary action. That is correct and should stay.
- **The four verification checks.** Concrete, specific, falsifiable.
- **Real category counts** next to every directory tag. Numbers that come from
  the database rather than from marketing.
- **The brand pair**, Deep Indigo `#3E3183` and Cornflower `#74A3FF`, already
  consistent between the logo and the interface.

## Biggest conversion opportunities

1. Strip the hero to four elements so the search field is unmissable.
2. Collapse five CTAs to two: one buyer intent, one supplier intent.
3. Move the strongest four statistics directly beneath the hero as proof, and
   delete the second band.
4. Give the project-fit matcher more prominence. It is the most differentiated
   interactive thing on the page and currently sits twelfth.

## Risks to manage

- **SEO.** The site exposes `/wp-json/` and carries Site Kit. Slugs, H1 text,
  internal link targets and structured data must survive any change. A visual
  redesign must not rewrite headings that rank.
- **Elementor coupling.** Changes made in the Elementor editor can be overwritten
  by template updates. A child theme stylesheet is safer than editor-level edits.
- **Analytics.** Renaming CTAs breaks historical comparison. Agree the CTA
  consolidation with whoever owns the funnel reporting before shipping.
- **Performance.** The trending and ranking rows load many cover images. Any
  carousel work should keep lazy loading and explicit dimensions to protect CLS.

## Conflicts between the four skills, and how they were resolved

- `high-end-visual-design` bans Inter outright. The user mandated DM Sans and
  Inter only, and `design-taste-frontend` permits Inter on explicit request.
  **The user's instruction wins.**
- `high-end-visual-design` asks for a pill eyebrow above every major heading.
  `design-taste-frontend` caps eyebrows at one per three sections. The brief
  names a design critic whose job is removing generic patterns, so **the cap
  wins**, and this is also audit finding 2.
- `remove-ai-design-slop` Part Three builds a 1080x1350 reference graphic, which
  is not this deliverable. **Part Two, the 29 tells, is applied as the audit
  checklist**; Part Three is not used.
