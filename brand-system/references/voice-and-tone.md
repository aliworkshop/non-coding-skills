# Voice & tone

The voice on a designed surface is Ali's prose style (`writing-style`) cut down to fit a page:
plain, declarative, concrete, and written for a reader who is smart and short on time. This file
adds what's specific to headlines, buttons, and microcopy.

`TODO(ali):` name the default reader for your own brand (developers? small-business owners? the
members of a consumer app?). Until then, ask which reader a surface is for before writing it.

## Hard rules

- **Direct second person.** "Your API stays up when traffic triples." Not "users will" or
  "businesses can."
- **Lead with the outcome, then the mechanism.** What changes for the reader comes first. How it
  works comes second, if at all.
- **Sentence case for headings.** "Is this for you?", "Frequently asked questions." Title Case
  only for proper nouns.
- **Two-clause sentences max.** If a line needs a third clause, it's two lines.
- **Concrete over abstract.** A number, a name, a time. "Deploys in 40 seconds" beats "fast
  deployments". Every number must be real; see `conversion-copy` on proof.
- **No exclamation points** outside small UI states.
- **No emoji** on marketing pages or stills.
- **No em dashes** on any designed surface. Use commas, colons, or two short lines.
- **No hype words.** Forbidden list below.

## Forbidden vocabulary

These words signal "a brand wrote this." Cut them on sight.

| Avoid | Use instead |
|---|---|
| unlock (figurative) | let you, make possible, (say what it does) |
| supercharge | speed up |
| revolutionize / transformative | change, replace the manual version |
| leverage (as verb) | use |
| seamless / frictionless / effortless | quick, simple, in the background |
| cutting-edge / state-of-the-art | (say what it does) |
| game-changing / next-level | (say what it does) |
| AI-powered | (say what it does) |
| robust / comprehensive | (show the specific property: tested, typed, monitored) |
| empower | (describe the outcome) |
| world-class | (cut; show, don't claim) |

Also banned: "Click here", "Submit", "Learn more", "Sign up today!", "Limited time offer."

## CTA microcopy

CTAs read like the next thing you'd say in person, with a trailing `→` as a literal glyph.

| Context | CTA |
|---|---|
| Book a call | `Book a call →` |
| Try the product | `Try it free →`, `Get the app →` |
| Open-source library | `Read the docs →`, `View on GitHub →` |
| Join a waitlist or community | `Join the waitlist →`, `Join the group →` |
| Contact | `Get in touch →` |

Persian equivalents are written natively, not translated word by word (`رزرو جلسه ←`,
`دانلود اپ ←`). In RTL the arrow points left. See `bilingual-copy`.

## Hero pattern

Eyebrow (optional, 2-4 words) → 2-line H1 with one concrete promise → one-sentence subhead with
the mechanism → one CTA. The H1 should be unsignable by a competitor: if any other product could
put the same line on its homepage, rewrite it.

## Pain-point cards

One sentence each, in the reader's words, naming a specific situation, not a category.
"Your Telegram bot stops answering when 500 people join at once" beats "scalability issues".

## Social proof

Real names and real numbers, with permission, or nothing. A quote from one real user beats a
logo wall that implies relationships that don't exist. Never write placeholder testimonials into
a page that might ship.

## Persian surfaces

Same rules, written natively in Persian: polite-neutral register (`شما`), Persian punctuation,
correct نیم‌فاصله, and no English fragments dropped into Persian sentences. `bilingual-copy`
holds the full checklist.
