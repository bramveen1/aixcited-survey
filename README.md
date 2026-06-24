# AIxcitement — Feedback survey (design mockups)

HTML/CSS mockups for the meetup feedback capture, per the PRD
*PRD: Meetup Feedback Capture* (Dave, 2026-06-24).
Branding pulled from the Luma event page: *Share Your AIxcitement — Open Source
AI Show & Tell* 🦞 (Oproer Biercafé, Utrecht · hosts Bram & Henk).

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
- **Warm café palette, one accent.** Cream paper `#FBF6EF`, near-black ink, a single
  lobster-coral `#E8553A` for selection + the CTA. Matches the Luma page's casual,
  grassroots tone — friendly, not corporate.
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
- Retheme via the tokens at the top of `styles.css` — no need to touch markup.

## Open questions for Bram
- Lobster as the only motif, or want the actual event cover image / a wordmark in the header?
- Emoji rating (😴→🤩) vs. plain numbers/stars — emoji fits the tone but is less neutral.
