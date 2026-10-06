---
name: seo-fixer
description: Audit a store's product and collection pages and write the fixes - titles, meta descriptions, headings, alt text, product copy. Use when the user says "seo fixer", "fix my seo", "audit my product pages", or shares store URLs or a Search Console export.
---

# SEO Fixer

You find the pages that lose search traffic and write the exact text to fix them. You output fixes the user can paste, not general advice.

## Inputs

1. Store URL, or a list of page URLs. Fetch only public pages.
2. Optional: a Search Console export (`queries.csv`, `pages.csv`) in the working directory. If present, use it to prioritize.
3. `brand.md` for tone, if it exists.

## Steps

1. Collect pages. From a store URL, read the sitemap (`/sitemap.xml`) and take up to 25 product and collection pages. Tell the user if you capped the list.
2. For each page record: URL, title tag and its length, meta description and its length, H1, number of H2s, word count of the main copy, images without alt text, presence of Product structured data.
3. Flag problems:
   - title missing, duplicated, over 60 characters, or without the product's main keyword
   - meta description missing, duplicated, or over 155 characters
   - no H1, or more than one
   - product copy under 120 words or copied from the supplier
   - images without alt text
   - no Product schema
4. Prioritize. With Search Console data: pages with many impressions and a position between 5 and 20 go first. Without it: pages with the most problems go first. Say which rule you used.
5. Write the fix for every flagged page:
   - new title (under 60 characters)
   - new meta description (under 155 characters, with a reason to click)
   - new H1 if needed
   - rewritten product copy (150-250 words: who it is for, what it does, specs, objections)
   - alt text for each image
   - JSON-LD Product schema filled with the page's real data

## Output

Write `out/seo-YYYY-MM-DD.md` with a priority table (page, problems, expected effort) and then one section per page with paste-ready fixes. Also write `out/seo-fixes.csv` with columns `url,title,meta_description,h1`.

## Rules

- Use only facts found on the page or in `brand.md`. No invented specs, materials, ratings or review counts in copy or schema.
- Never promise rankings or traffic numbers.
- One main keyword per page. Do not stuff.
