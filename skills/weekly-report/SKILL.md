---
name: weekly-report
description: Build a one-page weekly report on the user's store and its competitors from order exports and public competitor pages. Use when the user says "weekly report", "store report", "what changed this week", or "check my competitors".
---

# Weekly Report

You write one page the store owner reads in 3 minutes: what happened in the store this week, what competitors changed, and what to do on Monday.

## Inputs

1. Order exports in `data/` (CSV from Shopify, WooCommerce or any platform). You need at least: order date, order total, product name, quantity. Use discount code, country and traffic source columns if they exist.
2. Optional: ad spend per day in `data/ads.csv` (`date,channel,spend`).
3. `competitors.md` - a list of competitor store URLs. If it is missing, ask for up to 5 and save them.
4. `state/competitors-last.json` - the previous snapshot, if it exists.

Do not connect to store admin panels or ad accounts. Work from files and public pages.

## Steps

1. Load the exports with a short script (Python or the shell). Compare this week (last 7 full days) against the week before:
   - revenue, orders, average order value
   - top 5 products by revenue and the biggest mover up and down
   - share of orders with a discount code
   - if ad spend exists: spend, revenue per dollar of spend
2. Fetch each competitor's home page, best-sellers or main collection page, and up to 5 product pages. Record: product names, prices, sale banners, free shipping threshold, new products.
3. Diff against `state/competitors-last.json`. List only changes: price up or down, new product, removed product, new promo. Then overwrite the snapshot with today's data.
4. Write alerts. An alert is something that needs action this week: a competitor undercut a top product by 10% or more, a top product's sales dropped 30% or more, discount share above 40%.
5. Write 3 actions for Monday, each tied to a number from the report.

## Output

Write `out/report-YYYY-MM-DD.md`, one page:

```
WEEK AT A GLANCE   4 numbers with % change
WHAT MOVED         top products, biggest mover
COMPETITORS        changes only
ALERTS             0-3 items
DO THIS MONDAY     3 actions
```

## Rules

- Every number comes from the exports or a fetched page. If data for a block is missing, write "no data" in that block and say which file would fill it.
- On the first run there is no previous snapshot: report the current competitor state and say the diff starts next week.
- No padding. If nothing changed, say nothing changed.
