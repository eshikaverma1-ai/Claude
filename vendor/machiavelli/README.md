# Machiavelli

A Claude skill that reads a business situation for power and leverage, then writes the message.

You already know what you want. What is hard to see from inside a situation is who actually holds
the leverage, what the other side is really optimising for, and which of three plausible moves is
the one that works.

Paste the thread. Get back a power map, two or three ranked plays with what each costs, a
paste-ready draft, and the one move to avoid.

## Why Machiavelli

Because he is the most honest writer on power there is. His argument is that people act on
interest and fear of loss, and that pretending otherwise is how you lose.

That is the useful part. The cartoon version — lie, flatter, exploit — is the part that gets
people caught, and it is not what this produces. **Every play runs on true facts.** Real
deadlines, real alternatives, real numbers. Not on principle, on mechanics: a bluff that gets
called costs more than the deal was worth, and you only find out afterwards.

## The mistake it exists to stop

Measured on a real thread.

A brand named **$1,000**. The reply was a single figure **3.4x higher** with no alternative beside
it. They passed **four minutes later** — and a $1,000 product was sitting unoffered on the same
rate card the whole time.

A lone counter reads as a decline. The buyer closes the thread instead of taking it back to their
team, because you gave them nothing to take.

**Whenever they name a number, hold your headline rate AND put beside it one line they can buy at
the number they have.** Firmness lives in the rate. Flexibility lives in the menu.

Full breakdown in [`references/worked-example.md`](skills/machiavelli/references/worked-example.md).

## What you get back

Four things, in this order, and nothing else:

1. **The read** — one line. *"They are stalling because their budget resets in October, not
   because they have gone cold."*
2. **The power map** — one table: wants · fears losing · real alternative · clock pressure · who
   they answer to. The "fears losing" row does the work, because people move harder to protect
   what they have than to gain what they do not.
3. **Two or three plays**, ranked, each with what running it costs you.
4. **The message** — paste-ready, short, ending on a question rather than a number they have to
   reject.

Then one line on the move to avoid, and why it backfires. That line matters as much as the plays,
because most bad outcomes come from an obvious-looking move with a delayed cost.

**Draft only.** It never sends anything.

## Install

### Claude Code

```bash
/plugin marketplace add charlie947/machiavelli
/plugin install machiavelli
```

### Claude app (claude.ai)

**Fill in the three `your-context/` files BEFORE you zip it.** Once the skill is uploaded its
files live inside Claude and you cannot edit them — you would have to redo the whole upload. So:

1. Download this repo.
2. Fill in `skills/machiavelli/references/your-context/` (three files, see below). Or paste the
   folder into Claude Code and say "interview me" — it asks the questions and writes them for you.
3. Zip the `skills/machiavelli` folder.
4. **Customize → Skills → Add**, upload the zip.

The zip must contain the `machiavelli` folder at its root, not `SKILL.md` loose at the top —
otherwise it is rejected with "Missing required skill.md file".

### Any other agent

Copy `skills/machiavelli/` into wherever your tool keeps skills. It is four markdown files with
no dependencies, no scripts and no network calls.

## Set it up properly — this is the ten minutes that matters

Three files in [`skills/machiavelli/references/your-context/`](skills/machiavelli/references/your-context),
and they map onto the three rows of the power map that actually decide the outcome:

| File | Fills | The question people cannot answer |
|---|---|---|
| `01-what-you-want.md` | Wants | What sits BELOW your headline rate that someone could still buy? |
| `02-what-you-fear-losing.md` | Fears losing | What would you genuinely hate to lose here? |
| `03-your-real-alternative.md` | Real alternative | If this dies this week, what do you actually do instead? |

**Or let it interview you.** Say *"interview me"* — about fifteen questions, a few at a time. In
Claude Code it writes the three files itself. In the Claude app it cannot write to its own
uploaded folder, so it prints the finished files in the chat for you to save locally and
re-upload. Either way you get better answers than a blank template does.

**It never blocks on this.** Paste a thread before you have filled anything in and you still get
the read — it just says which rows it had to guess, and offers the interview afterwards. A tool
that demands setup before it will answer the question you came with is a worse tool.

**Why three files and not one.** They are answered at different times and change at different
speeds: a rate card moves yearly, a fear moves with one bad month, an alternative moves the day a
new client lands. And people will tell you what they want long before they will write down what
frightens them, so asking for both on one page gets you one honest section and one polite one.

**The one people skip is the second file**, and it is the one that matters. Machiavelli's actual
observation is that people work harder to protect what they have than to gain what they do not.
Whoever has more at risk in a given exchange is the one who gives ground — so a map with an
honest "wants" row and a fudged "fears losing" row produces confident advice that is wrong in the
only place it counts.

Without these it still runs, but it is guessing at what you can walk away to and how easily they
replace you. That is the difference between a read and a horoscope.

## Use it

Paste a thread and ask what to do. No need to name the skill:

- *"They've gone quiet, what do I do?"*
- *"What's my leverage here?"*
- *"They came back at $1,000. How do I play this?"*
- *"Should I walk?"*
- *"Who actually decides this?"*

You do not need to summarise the thread first, and you should not. **The original wording carries
the tells** — [`references/reading-the-thread.md`](skills/machiavelli/references/reading-the-thread.md)
lists the ones worth reading for. A deadline mentioned twice is real. *"When could you start?"*
before terms means they have already told someone internally it is happening. Silence after
enthusiasm is almost never disinterest — it is an internal blocker you cannot see.

## What it will not do

- **No plays against your own team.** Staff are not counterparties. That is a communication
  problem with a documented answer, not a campaign.
- **No manufactured urgency, invented competing offers or fake scarcity.** See above — mechanics,
  not morals.
- **It never sends anything.** Every draft is yours to edit and send.
- **It does not do pricing.** It reads the situation and holds whatever rates you put in your
  leverage file. What to charge in the first place is a different question.

## The failure mode it watches for in itself

The pull is towards a clever-sounding campaign — sequences, timings, engineered impressions. Most
real situations resolve on one honest sentence sent to the right person at the right moment, and
the value is working out which sentence and which person.

If the draft runs longer than six lines, the read was probably wrong.

## Licence

MIT. Do what you like with it.

Built by [Charlie Hills](https://charliehills.substack.com).
