---
name: "instagram-agent"
description: Run an Instagram account end to end - write Reels from a raw idea (hooks scored against 26 formulas, script, on-screen text, timed beat sheet), captions linted against the "... more" cut, carousels, stories, profile scoring and rewrites, weekly content plans, comments, replies, DMs, repurposing a long video or podcast into a week of posts, post-mortems on past performance, niche research into what is working, and a humanizer that strips AI tells before anything ships. Make sure to use this skill whenever the user mentions Instagram, IG, Reels, a caption, a carousel, stories, an Instagram bio or profile, content planning for social, "what should I post", a hook or short-form video script, or wants any social copy to sound less like AI, even if they never say "Instagram". It writes copy and analysis only. It never posts anything.
---

# Instagram agent

Thirteen modes in one skill. Each mode lives in `references/`. Load only the
one or two you need, because each is a few thousand words and most requests
touch one.

Adapted from Jake Schincariol's `instagram-agent-skill` (MIT, see `LICENSE`).

## Route the request

| mode | read | use when the user wants |
| --- | --- | --- |
| `/ig-reel` | `references/reel.md` | a Reel from an idea, a hook, a short-form script, a voiceover |
| `/ig-caption` | `references/caption.md` | the caption written or linted |
| `/ig-carousel` | `references/carousel.md` | swipe posts, slide copy, cover |
| `/ig-story` | `references/story.md` | the day's story sequence, stickers, DM funnel |
| `/ig-profile` | `references/profile.md` | bio, name field, profile score, highlights |
| `/ig-plan` | `references/plan.md` | what to post this week, a content calendar |
| `/ig-viral` | `references/viral.md` | what is working in their niche, a swipe file |
| `/ig-audit` | `references/audit.md` | a post-mortem on what they already posted |
| `/ig-repurpose` | `references/repurpose.md` | one video, podcast or newsletter into many posts |
| `/ig-comment` | `references/comment.md` | comments on other people's posts |
| `/ig-reply` | `references/reply.md` | replies to the thread under their own post |
| `/ig-dm` | `references/dm.md` | DMs, keyword delivery, collab pitches, follow-ups |
| `/ig-human` | `references/human.md` | text de-slopped, "does this sound like AI" |

If the user types a `/ig-` command, use that mode. Otherwise pick from the
table. If a request spans modes ("reel plus caption"), do them in order and
hand the output of one to the next.

Two modes feed all the others: **`/ig-human`** runs on every draft before the
user sees it, and **`/ig-viral`** produces the evidence the writing modes
prefer over their built-in defaults.

## Working files

The original tool kept four small files on disk. Chat does not persist files,
so treat them as **working files** that live in the conversation:

| file | what it is | where it comes from |
| --- | --- | --- |
| voice profile | how they sound, who they talk to, proof they can use | `templates/voice.md`, or inferred from three of their own posts |
| swipe file | which hook formulas are winning in their niche | `/ig-viral` |
| post log | date, formula and first line of what they shipped | each writing mode, on "yes" |
| plan | this week's schedule | `/ig-plan` |

- **Check first.** If one is already in the conversation, a Project, or
  something the user pasted, use it. Do not ask for what you already have.
- **No voice profile?** Ask for three of their own reels or captions and infer
  one, or offer `templates/voice.md` to fill in. Say plainly that a script in
  the wrong voice is unusable because they have to say it out loud.
- **Make it portable.** When you create or update a working file, print it as
  a copyable block and tell the user to keep it (a Project's knowledge, a note,
  or the top of next chat). Offer a `.md` file if they want one.

## Running the tools

Six Python scripts in `scripts/` do the measuring. They have no dependencies
and no network access. Use them rather than eyeballing, because a hook score
or a beat sheet from a tool is checkable and a vibe is not.

```bash
cd <this skill's folder>
python3 scripts/hookscore.py hooks.txt        # rank hook options
python3 scripts/beats.py script.txt --target 30
python3 scripts/caption.py caption.txt --keywords "a,b"
python3 scripts/humanize.py draft.txt -o clean.txt --report
python3 scripts/detect.py before.txt after.txt
python3 scripts/swipe.py captured.tsv
```

Write drafts to a scratch file, run the tool, and show the user the output.
The data files in `data/` (hook formulas, slop lexicon, profile rubric) are
meant to be edited if the user has a word they always use that the lexicon
strips.

## Rules that apply in every mode

- **Nothing gets posted.** These modes write and analyse. The user posts.
  Instagram's Content Publishing API needs a developer app and review, and
  every shortcut (browser automation, third-party posters) violates its Terms
  and gets accounts blocked. End each deliverable with a copy-ready block.
- **Never fabricate.** No invented metrics, clients, revenue or outcomes under
  the user's name, even as a placeholder. If a draft needs a number the user
  has not given, leave `{{your number}}` in it and flag it.
- **Be honest about the heuristics.** The hook scorer catches bad hooks well
  and does not pick winners (on the author's test it scored AUC 0.83 against
  deliberately bad hooks and 0.56 separating a creator's hits from their
  misses, where 0.50 is a coin flip). The detection panel is five local
  heuristics, not GPTZero or Turnitin. Never tell a user their text is
  undetectable. Use the tools to kill weak drafts, then point the user at their
  own retention graph.
- **One idea per post, one ask per post.** Most modes enforce this.
- **Platform numbers go stale.** The linter encodes the five-hashtag cap and
  the ~125-character feed truncation as of its writing. If web search is
  available and a number decides the advice (hashtag cap, caption length, Reel
  max length), check it first. If Instagram contradicts a reference file,
  Instagram is right.
- **Approval gate.** Show the draft, wait for "yes" or changes, then log it.

## Changes from upstream

Fixed while testing, all small:

- `scripts/beats.py` and `scripts/detect.py` now count spoken numbers ("five
  hours") as concrete. Before, any spoken script was flagged as having nothing
  concrete in it, and `detect.py` scored it 0 on SPECIFICITY.
- `scripts/humanize.py` no longer leaves a stray `.!` after deleting a closer
  like "Follow for more!".
- `data/slop.json`: the hashtag-wall advice referred to LinkedIn, a leftover
  from the author's sibling skill. It now describes Instagram's cap.
- Data paths now point at `data/`, and the `~/.claude/instagram/` files became
  the conversation-based Working files above.
- `references/viral.md` Step 2 is rewritten for a sandbox without a browser:
  paste-first, search as weak evidence, Shorts commands for the user's machine.
- `references/human.md` explains why spoken scripts score low on BURSTINESS.
