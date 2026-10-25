---
name: training-proposal
description: Draft proposals and outlines for technical training Ali offers (Go, backend engineering, AI engineering / LLM agents, team workshops) from unstructured notes, convert the markdown to a branded PDF, and read past .pdf proposals for reference. Covers client proposals, workshop syllabi, bootcamp and course outlines, session agendas, pricing quotes, and scoping. Triggers: "draft a proposal for X", "write the workshop outline", "quote this training", "turn these notes into a syllabus", "make the PDF", "یه پروپوزال برای ورکشاپ بنویس".
---

# Training Proposal

Draft, edit, and convert proposals for technical training and workshops Ali delivers: Go and
backend engineering, AI engineering (agents, tools, durable execution, evals), and hands-on team
sessions. Branding (logo, fonts, colors) comes from `brand-system`. Session content and
sequencing come from `workshop-planner` when the curriculum isn't settled yet.

## Workflow

1. **Gather info** from Ali (or the notes).
2. **Draft markdown** following the most recent proposal of the same type.
3. **Ali reviews and edits** the markdown.
4. **Convert to PDF** with the bundled pipeline.

## Reading past proposals

```bash
cd ~/.claude/skills/training-proposal/scripts && uv run python read-pdf.py /path/to/proposal.pdf
```

Past proposals live in one folder per client: `<proposals-root>/<client>/`.
`TODO(ali):` set the proposals root.

## Updating a proposal

Read the existing markdown, make targeted changes, and re-save. Don't regenerate from scratch.

When a value appears in more than one place (durations, session counts, titles, structural
terms), update every instance: the syllabus Duration, session headers, Investment rows, the
Total, and payment terms. Re-check the arithmetic after any duration or price edit. A priced
document loses trust the moment the numbers don't add up.

## Drafting a proposal

**Start from the best base.** Look across *all* client folders and pick the **most recent
proposal of the same offering type**. It carries the latest wording. Rank by the `Prepared on`
date inside each file, not by file mtime (editing an old file floats it to the top):

```bash
for f in */*team*.md; do d=$(grep -m1 '^\*Prepared on' "$f" | sed 's/^\*Prepared on //; s/ by .*//'); echo "$(date -j -f '%B %d, %Y' "$d" '+%Y-%m-%d' 2>/dev/null) $f"; done | sort -r
```

Variant tokens: `team` (group workshops), `1on1` (individual or pair coaching), `course`
(multi-session course or bootcamp), `retainer` (ongoing support). Skip files with `example` in the
name. If nothing exists yet, use `references/format-reference.md` as the skeleton.

Gather (ask for anything missing):

- **Client** and **audience** (roles, level, stack, team size)
- **Training title**
- **Sessions** and **duration** each
- **Delivery** (Google Meet, Zoom, Teams, in person) and **language** (English or Persian; a
  Persian proposal is written natively, see `bilingual-copy`)
- **Topics per session**, or themes to flesh out
- **Prerequisites and setup** attendees need (Go version, API keys, repo access)
- **Pricing.** `TODO(ali):` standard rates and currency. Until set, ask every time. Never invent
  a rate. Price custom sessions as `duration_hours × rate`.
- **Discount** — list sessions at full price, then a green discount row:
  `| <span style="color: #2E7D32">*Discount*</span> | | <span style="color: #2E7D32">*-$X*</span> |`.
  The Total reflects the discounted price.
- **Dates** (or TBD)

**Structure.** Multiple sessions, or one session with parts (`### Part 1:`). The syllabus
Duration says which ("4 sessions (90 min each)", "1 session (3.5 hours total)").

**Flexible scope.** When the count isn't settled, price by building block (each unit at its unit
price) and give two example scopes, small and large, each with a reconciled Total. Define any term
that could be read two ways right before the table.

**Next phases (only when asked).** A short list of follow-on offerings at unit prices after the
Investment, kept out of the Total.

**Two sources, two jobs.** Copy comes from the most recent live proposal of the same type.
Format comes from `references/format-reference.md`, a content-free skeleton of every structural
pattern (syllabus table, spacer row, parts, timed segments, optional segments, page break, both
Investment table shapes, `Included` and `n/a` cells, discount row, payment terms).

**Filename.** `<proposals-root>/<client>/proposal_<client>_<variant>.md`. H1:
`# <Training Title> - <Client>`. The PDF inherits the basename. No `_v2` or date suffixes; edit in
place. `<client>` is kebab-case.

Tell Ali to review the markdown before generating the PDF.

## Voice & Style

A proposal is a spec, not a pitch. The deal sells itself through clear structure; persuasion belongs in the cover email and the live conversation. Write to define what happens, and cut anything whose job is to convince or impress. Drafting in this voice up front saves the user from stripping it down later.

- **Compress to the outcome.** State the result; don't explain the mechanism inside it. "Each participant ships one working agent against their own API" beats "three agents built live (12 total), drawn from the intake form, plus one built as homework."
- **One idea per sentence.** Any punctuation that fuses two clauses into one breath (em-dash, semicolon, comma-splice) is a signal to split into two sentences or cut the trailing clause. A period is almost always the fix. (These get edited out every time.)
- **No em dashes or en dashes, anywhere.** Not in prose, not in headers, not as table placeholders. They read as machine-written, so write without them from the start. Replace a prose em dash with a period, comma, or colon. Write number ranges with a hyphen ("2-3 skills", "3-4 participants"), not an en dash. Use "n/a" for an empty Investment-table cell, not "—".
- **Cut rationale and framing.** A well-ordered agenda argues for itself. Don't narrate why it's structured that way ("no demos here, those come later") or add an "Our Approach" essay. Meta-commentary reads as insecurity about the structure. *One sanctioned exception:* a short "Why this matters" block under the Engagement Goal, only when Ali asks for it. Keep it to ~2 bullets on what the team can do afterwards. Don't let it grow into an essay.
- **The client is the hero, not the instructor.** Demote yourself as the actor, promote the team as the one who acts and benefits. You get the work verbs (instruct, demo); they get the outcome verbs (learn, build, share). Prefer "services the team can ship" over "services to ship," and "Instructor builds…" over "I build…".
- **Don't tally or label-inflate.** Counts ("12 agents!") and marketing terms ("done-for-you") signal salesmanship and quietly commit you to numbers. Promise the minimum you can stand behind.
- **Name things plainly.** Calm, true nouns over benefit-reaching labels: "Building Reliable LLM Agents in Go" over "Unlocking AI-Powered Engineering Excellence."
- **Say each thing once.** If info already lives in its natural place (the table, the body), don't echo it in the overview or repeat structural prefixes ("Session 1:") that the ordering already conveys.
- **Spend words only where they're load-bearing.** Ruthless on adjectives, precise on commitments and logistics. Hard constraints like "filled out no later than 7 days prior" or "30-minute debrief" earn their length because they protect delivery.

Rhythm: short, present-tense, subject-verb-object declaratives. Modest active voice. No stacked "which/that" clauses.

## Converting to PDF

Before converting, verify:

- Each session's timed segments sum to its stated duration.
- The Investment table reconciles to the headline **Total** on both axes, and the two axes are independent:
    - **Total Duration** = the sum of every stated duration in the Duration column, including rows priced **Included**. An `Included` deliverable with a real duration (e.g., a 30-min Check-In Call) is committed delivery time, so its minutes count toward the Total hours even though it contributes nothing to the price. Only rows with no stated duration (`n/a`) are skipped.
    - **Total Price** = the sum of the dollar rows only. `Included` rows contribute nothing to the price.
    - Worked example: 3 x 90-min workshops + a 30-min Included Check-In Call = **5 hours total** at the same workshop price (not 4.5 hours). The 4.5-hour answer is the classic mistake: don't drop an Included row's duration from the Total.
- **Genuinely optional segments** (e.g., "optional 15-min Q&A after the session") are the only thing excluded from both the Total duration and price. "Optional" means the client can decline it. It is not the same as "Included" (committed, no extra charge). The same duration reads identically in the session header, the Investment row, and the Total.
- Titles, durations, and structural terms read identically everywhere they appear.

After the user approves the markdown:

```bash
cd ~/.claude/skills/training-proposal/scripts && uv run python md-to-pdf.py /path/to/outline.md
```

The PDF is created in the same directory as the markdown file, with the same base name (`.md` → `.pdf`).

## Formatting Notes

These conventions aren't obvious from the example alone — follow them for correct PDF rendering:

- Syllabus uses HTML `<table class="syllabus">` with `<tr class="spacer">` to separate title/instructor from dates/logistics (not a markdown table)
- Use `TBD` for unknown dates/times — it gets highlighted in red in the PDF
- Each session's timed segments should add up to the session duration
- Session content uses: `- **Section** *(15 min)*` with nested bullets for subtopics
- Use `---` horizontal rules between sessions
- Use `<div class="page-break"></div>` before the Investment section to force a page break
- Inline HTML like `<span style="color: #2E7D32">` works inside markdown table cells for colored text (e.g., discount rows)
- For an asterisk note under a session (a caveat about how a segment works), wrap it in `<p class="footnote">...</p>`. The `.footnote` class in `style.css` renders it ~20% smaller and gray, so it reads as a subordinate note rather than body copy
- Investment table goes at the end with a bold **Total** row — use consistent unit formatting across all rows
- Prepared-by line format: `*Prepared on <date> by Ali Torabi*` (italicized, includes date)
- Payment terms go after the Investment table as a `### Payment terms` subsection with bold bullet labels
