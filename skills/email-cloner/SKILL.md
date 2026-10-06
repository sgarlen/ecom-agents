---
name: email-cloner
description: Break down competitor email campaigns and rebuild them for the user's brand. Use when the user says "clone emails", "email cloner", "adapt this campaign", or pastes or forwards competitor emails.
---

# Email Cloner

You turn competitor emails into ready-to-send emails for the user's brand. You copy the structure and the timing, never the wording.

## Inputs

1. `brand.md` in the working directory. If it is missing, ask for: brand name, product, price, audience, 3 proof points, tone of voice, banned words, current offer. Save the answers to `brand.md`.
2. Competitor emails: pasted text, `.eml` or `.html` files in `inbox/`, or screenshots. Ask the user which flow each email belongs to if it is not obvious (welcome, abandoned cart, post-purchase, winback, promo).

Work only with emails the user provides. Do not access any mailbox.

## Steps

1. Build an inventory table: sender, date, subject line, preview text, flow, main offer, call to action, length in words.
2. If several emails come from one sender, reconstruct the sequence: order, days between sends, how the offer changes from email to email.
3. For each email worth keeping, write the breakdown:
   - subject line pattern (curiosity, number, personal, urgency, plain)
   - block order (hero, story, proof, offer, CTA, PS)
   - the one job of this email
4. Rebuild each one for the user's brand:
   - 5 subject lines (under 45 characters) and matching preview text
   - full body copy in plain text, with block labels
   - one CTA, repeated at most twice
5. If you reconstructed a sequence, output the full flow with send delays.
6. Check against `brand.md`: no unbacked claims, no banned words, no copied sentence longer than 4 words.

## Output

Write `out/emails-YYYY-MM-DD.md`: inventory, breakdowns, rebuilt emails, and the flow map. End with the 2 subject lines you would A/B test first and why.

## Rules

- Never invent discounts, deadlines or stock levels. Use the offer from `brand.md` or leave `[OFFER]`.
- Keep emails short: one idea per email.
- If the user gave only one email, rebuild it and suggest the 2 emails that would normally follow it in that flow.
