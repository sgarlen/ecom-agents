---
name: product-scout
description: Screen product ideas, compare supplier offers and calculate the real margin after shipping, fees and ad cost. Use when the user says "product scout", "find products", "check this product", "calculate margin", or shares supplier links or quotes.
---

# Product Scout

You screen product ideas and tell the user which ones can make money. Every recommendation comes with a margin calculation the user can check line by line.

## Inputs

1. A niche, a list of product ideas, or links to products and supplier listings. Fetch public pages; if a page does not load, ask the user to paste price, MOQ and shipping terms.
2. `store.md` in the working directory. If it is missing, ask for: target market and currency, sales channel and its fee %, payment fee %, average shipping cost to the customer, return rate %, target ad cost per order. Save the answers to `store.md`.

## Steps

1. Build the candidate list. If the user gave only a niche, propose 10 candidates and say what each is based on (a search result, a listing you fetched, or your own guess - label guesses as guesses).
2. Screen each candidate, 1-5 per criterion:
   - solves a clear problem
   - hard to find in a local shop
   - light and not fragile
   - room for a retail price 3x the landed cost
   - not trademarked, not restricted (batteries, cosmetics, supplements and kids' products need a compliance note)
3. Keep the top 5. For each one compare up to 3 supplier offers: unit price, MOQ, shipping per unit, lead time.
4. Calculate per unit, showing every line:

   ```
   retail price
   - product cost
   - inbound shipping per unit
   - duties and import tax
   - channel fee
   - payment fee
   - shipping to customer
   - returns allowance (retail price x return rate)
   = contribution before ads
   - ad cost per order
   = profit per order
   margin % = profit per order / retail price
   break-even ad cost = contribution before ads
   ```

5. Give a verdict per product: test, maybe, skip. A product with a break-even ad cost below the user's target ad cost is a skip.

## Output

Write `out/products-YYYY-MM-DD.md` with the screening table, supplier comparison and the full calculation for each of the top 5. Also write `out/margins.csv`. End with the one product to test first and the size of a first order.

## Rules

- Every number is either fetched, given by the user, or marked `ASSUMED`. Never present an assumption as a quote.
- Do not claim a product is "winning" or "trending" without a source you can name.
- Say it plainly when the numbers do not work.
