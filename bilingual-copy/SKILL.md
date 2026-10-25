---
name: bilingual-copy
description: >
  Write, translate, and localise user-facing text between English and Persian (فارسی) for
  Ali's products: app UI strings, error messages, push notifications, onboarding screens,
  App Store / Play / Telegram bot listings, emails, and announcements. Use whenever Ali asks
  to "translate this to Persian", "write the fa version", "localise these strings", "check my
  Persian copy", "این رو انگلیسی کن", "ترجمه کن", or hands over a strings/TOML/JSON file with
  en and fa entries. Also use when reviewing Persian text for ZWNJ, punctuation, or RTL
  issues. Do NOT use for chatting in Persian — just answer in Persian.
---

# Bilingual Copy (English ⇄ فارسی)

Both languages are first-class. The Persian is not a translation of the English; it is the
same message written by someone who thinks in Persian. A Persian reader should never be able
to tell which version came first.

## The rules

**Translate the meaning, not the words.** Rebuild the sentence in natural Persian order
(subject … object … verb). English idioms get a Persian equivalent or a plain statement, never
a literal copy. "You're all set!" → `همه‌چیز آماده است` or `تمام شد!`, not `شما همه تنظیم شدید`.

**Don't interpolate English fragments into Persian.** When an English message embeds a value
that is itself English (a status word, a purpose, a list of field names), the Persian says the
same thing without it, and the value still reaches the client as a separate property:

```toml
# en
[InviteNotPending]
other = "this invite is {{.status}}, not pending"
# fa
[InviteNotPending]
other = "این دعوت دیگر در انتظار پاسخ نیست"
```

Numbers and names interpolate fine in both: `حداکثر {{.max}} علاقه‌مندی می‌توانید انتخاب کنید`.

**Every key exists in both files.** A key missing from one language either falls back to the
other language or shows the raw key. When adding, renaming, or removing a key, do both files
in the same change, and say if a project check (like `make errors-check`) should be run.

**Register.** Default to polite-neutral `شما` with plural verbs (`وارد شوید`, `لطفاً دوباره
تلاش کنید`) for app UI and errors. Use friendly `تو` only when the product's existing copy
already does. Never mix the two in one product.

**Keep it short in UI.** Buttons are a verb, 1-2 words: `ادامه`, `ذخیره`, `ارسال کد`.
Persian often runs longer than English. If a string must fit a fixed width, say so and offer
a shorter variant.

## Orthography checklist

- **نیم‌فاصله (ZWNJ, U+200C)** in prefixes and suffixes: `می‌شود`, `نمی‌توانید`,
  `درخواست‌ها`, `خانه‌ام`. A space or no gap here is the most common error. Check by searching for ` ها `, `می ` and `ها` glued to Latin text.
- **Persian letters, not Arabic:** `ی` (U+06CC) not `ي` (U+064A); `ک` (U+06A9) not `ك` (U+0643).
- **Punctuation:** `،` comma, `؛` semicolon, `؟` question mark. Guillemets `«»` for quotes.
  No space before punctuation, one after.
- **Digits:** follow the product's convention and keep it consistent. Persian digits
  (`۱۲۳`) for running text when the app localises numbers; Latin digits inside codes, OTPs,
  phone numbers, prices in a field the user copies, and anything a user types back.
- **Mixed direction:** Latin words inside Persian (brand names, `iOS`, an email address) are
  fine. Watch the ends of lines, where a Latin word or a number next to punctuation can flip
  visually in RTL. If a string starts with a Latin word, flag it so the UI can set direction.
- **Dates:** Persian UI shows the Solar Hijri (شمسی) calendar unless the product says
  otherwise: `۴ آبان ۱۴۰۵`. Don't convert dates in stored data, only in display copy.

## Workflow

1. **Get the context.** What screen or channel, who reads it, the character limit if any,
   and the existing copy's register. If there's an existing strings file, read it first and
   match its tone and terms.
2. **Keep a glossary consistent.** Reuse the terms the product already uses (if it says
   `رویداد` for event, don't switch to `ایونت`). When a new term is needed, propose one and
   note it.
3. **Write both versions**, side by side, keyed:

   | key | en | fa |
   |---|---|---|
   | `OtpSent` | We sent a code to {{.phone}} | کد تأیید به {{.phone}} ارسال شد |

4. **Flag what needs Ali's call:** a term with no clean Persian equivalent, a string that
   won't fit, a tone change from the existing copy. One line each.

## Editing strings files

Edit TOML/JSON/YAML as text and change only the keys involved. Don't reserialise the whole
file, it reformats everything and buries the change in the diff. Validate the file parses
after editing.

## Reviewing Persian someone else wrote

Report in the `skimmable-summary` shape: counts, then sections for Meaning, Orthography
(ZWNJ, letters, punctuation), Register, and Consistency, each issue as `key — problem —
suggested fix`. Don't rewrite strings that are already right.
