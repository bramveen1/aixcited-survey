# AIxcitement — Feedback survey (design mockups)

HTML/CSS mockups for the meetup feedback capture, per the PRD
*PRD: Meetup Feedback Capture* (Dave, 2026-06-24).
Branding pulled from the AIxcitement logo + announcement page: *Share Your
AIxcitement — Open Source AI Show & Tell* (Oproer Biercafé, Utrecht · hosts
Bram & Henk). The official logo lives at `assets/aixcitement-logo.png`.

## Files
| File | What it is |
|------|------------|
| `index.html` | **During-event** form. QR → phone, one screen, no page breaks, sub-30s. |
| `email.html` | **Post-event email** variant. Same fields, past-tense, one extra optional question. |
| `styles.css` | Shared design tokens + components. Edit tokens at the top to retheme. |

Open either file in a browser. Submit is faked client-side to show the
thank-you state — there is no backend here.

## The five fields (from the PRD)
1. **Rating** — 1–5 emoji scale (required)
2. **Do it again?** — Yes / Maybe / Nah (required)
3. **One thing to change** — open text (required)
4. **Want in on the next one?** — checkboxes: organise / speak / keep me posted (optional)
5. **Email** — revealed *only* when a box in Q4 is ticked, required then (anonymous otherwise)

The email variant adds a 6th, optional "anything that stuck with you?" — the PRD's
"more time, so ask a bit more" note. Nothing else differs.

## Design decisions
- **Dark announcement-page palette, colours straight from the logo.** Deep navy ground
  `#02051B`, white ink, electric cyan `#00EFFA` ("AI") as the single interactive accent
  (selection + CTA), lime green `#75F97F` (the X highlight) reserved for positive/success
  moments (the thank-you). Cyan CTA carries dark navy text for high contrast.
- **Real logo in the header, inlined as SVG.** The wordmark is inlined directly in the
  markup (vector `assets/aixcitement-logo.svg` is also in the repo). Inlined rather than
  `<img src>` because external SVGs loaded via `<img>` often fail to pull the Bricolage
  Grotesque webfont, silently falling back and breaking the wordmark — the font is loaded
  via Google Fonts in `<head>`. Crisp on a projector. The logo is built for a dark
  background, which is why the surface is navy. `aixcitement-logo.png` is kept as the
  email-safe raster (see Sam note below).
- **Anonymous by default.** Email is hidden until the attendee opts in. No accounts,
  no tracking — matches PRD scope.
- **Phone-first, big targets.** 52px minimum tap targets, 16px inputs (no iOS zoom),
  emoji rating for fast thumb input while standing with a drink.
- **One screen, no page breaks** — every tap loses people mid-event.

## Notes for Sam (handoff)
- Architecture, storage, real submit, and per-event tagging are **your call** — this is
  design only. The PRD requires the organiser to tell events apart; a `?event=` slug or
  hidden field is the obvious hook but I left it to you.
- The conditional email reveal uses a few lines of JS. **Email clients strip `<script>`**,
  so in `email.html` it degrades to "email always visible, optional" when JS is off — fine,
  but worth knowing.
- **Inline SVG renders in a browser preview but most email clients (Gmail, Outlook) strip
  or ignore it.** For the *actual sent email*, swap the inline SVG for the hosted
  `aixcitement-logo.png` (raster, email-safe) — it's left in `assets/` for exactly this.
  The inline SVG is the right call for the web app (`index.html`); the PNG is the right
  call for the real email send.
- Retheme via the tokens at the top of `styles.css` — no need to touch markup.

## Open questions for Bram
- ~~Logo SVG~~ — resolved: SVG supplied and inlined. ✓
- ~~Lobster wink in CTA + thank-you~~ — resolved: keep it. ✓
- ~~Emoji rating vs. numbers/stars~~ — resolved: keep emoji. ✓
- No open design questions — ready for Sam.
