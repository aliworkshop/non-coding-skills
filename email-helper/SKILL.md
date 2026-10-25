---
name: email-helper
description: >
  Draft emails and work messages in Ali's voice, in English or Persian: replies, follow-ups,
  declines, introductions, scheduling, client and recruiter emails, messages to a lead or
  teammate, and Telegram/Slack messages that need the same care. Use ANY time Claude is
  composing an email or a message Ali will send to someone, including when another skill is
  running and an email is one step of it. Triggers: "draft a reply", "write an email to",
  "respond to this", "follow up with", "how do I say no to this", "یه ایمیل بنویس", "جوابش رو
  بده". For emails whose job is to sell or convert, hand off to conversion-copy; for a live
  negotiation, use tactical-negotiation for the moves and this skill for the wording.
---

# Email Helper

Ali's voice is the `writing-style` skill applied to a message: direct, warm, short, and always
moving the conversation forward. Read that skill's rules; this one adds what is specific to
email and messages.

No mail connector is assumed. Draft in the chat, ready to paste, unless a Gmail or Outlook tool
is connected and Ali asks for a draft there. Never send anything. Ali sends.

## Before drafting

**Read the thread, not the summary.** Ali's description is the intent; the thread is the
context. If the message being replied to isn't in the conversation, ask for it (pasted text or
a screenshot) rather than drafting blind. Build the reply from what the other person actually
wrote: their questions, their dates, their words.

**Pick the language and register from the thread.** Reply in the language they wrote in. In
Persian, match their formality: `جناب آقای / سرکار خانم` and `با احترام` for formal or
first-contact mail; a first name and `ممنون` with a colleague. In English, "Hi [Name]," for
first contact, "Hey [Name]," for people Ali knows. Never "Dear Sir/Madam".

## Voice

- **Lead with the answer.** If they asked a question, the first line answers it. No
  "Hope you're doing well", no "Great question", no restating their email.
- **One idea per paragraph, 1-2 sentences each.** It should read easily on a phone.
- **Every email ends with one clear next step**: a question, a time, a link, a decision. The
  exception is a closer ("Done, merged.") where closing the loop *is* the point.
- **Two asks? Number them.** "Two things:" then a numbered list, each item ending with their part.
- **Digits, not words:** "3 days", "$40/hr", "v1.4".
- **No em dashes** in English emails. Use a period or a comma. They read as machine-written.
- **No bold, no headings** in normal emails. It should look like a person typed it.
- **Sign-off:** "Thanks, Ali" for first contact and formal mail; "Cheers, Ali" or "-Ali" for
  people Ali knows; nothing at all in a fast back-and-forth. Persian: `با تشکر، علی` (formal) or
  `ممنون، علی`.

## Situations

**Saying no.** Lead with the path forward, fold the reason into a clause, no "Unfortunately",
no apology: "While I can't take this on before December, I could start on the 2nd if that
still helps." Persian: "با توجه به حجم کار فعلی تا آذر امکانش را ندارم، ولی از دوم آذر در خدمتم."

**Pushing back on scope or a deadline.** State what's possible and what it costs, not what's
impossible: "I can ship the API by Friday without the admin panel, or both by the following
Wednesday. Which matters more?" For anything tense, take the move from `tactical-negotiation`.

**Recruiters and contract offers.** Short, friendly, and specific about what Ali wants (role
type, remote or not, rate). Ask the one question that decides whether it's worth a call.
Never state a number first unless Ali gave one to use.

**Reporting a problem or an incident to a team or client.** What happened, the impact, what's
been done, what's next and when. No blame, no adjectives. Link the issue or PR.

**Follow-ups.** Shorter each time. Don't re-pitch, just nudge, on the same thread:
"Just checking in on this. Would Thursday work?" Persian: "خواستم پیگیری کنم. پنجشنبه براتون مناسبه؟"

**Introductions.** Two lines per person: who they are and why they should talk. Move the
introducer to BCC on the reply.

**Scheduling.** Offer 2-3 concrete slots with the timezone written out (`Tue Oct 28, 15:00-17:00
Tehran time (UTC+3:30)`) when the other side might be elsewhere. One slot inline for a quick
follow-up. Confirm the timezone with Ali the first time it matters; don't assume it.

## Telegram and chat messages

Same voice, shorter. No greeting line on an ongoing chat. One message, not three. If it needs
more than ~5 lines, it's probably an email or a doc.

## Output

Give the draft in a fenced block so it copies cleanly, subject line first when it's an email.
If there's a real choice of approach (firm vs. soft, short vs. detailed), give two versions
and say which you'd send and why. Otherwise give one.
