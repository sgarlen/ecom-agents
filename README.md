# ecom-agents

Five skills for Claude Code that work as a small e-commerce team.

| Skill | What it does | What you give it |
|---|---|---|
| `ad-cloner` | Breaks down competitor ads and rewrites the strongest ones for your brand | Pasted ads, screenshots or public ad library links |
| `email-cloner` | Breaks down competitor emails and rebuilds the campaigns for your brand | Pasted or forwarded emails |
| `seo-fixer` | Audits product pages and writes paste-ready titles, descriptions, alt text and schema | Your store URL, optional Search Console export |
| `product-scout` | Screens product ideas, compares suppliers, calculates margin line by line | A niche, product links or supplier quotes |
| `weekly-report` | One page on your store and your competitors, with 3 actions for Monday | Order export CSV, list of competitor URLs |

## Install

macOS / Linux / Git Bash:

```bash
git clone https://github.com/sgarlen/ecom-agents && mkdir -p ~/.claude/skills && cp -r ecom-agents/skills/* ~/.claude/skills/
```

PowerShell:

```powershell
git clone https://github.com/sgarlen/ecom-agents; New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null; Copy-Item -Recurse -Force ecom-agents\skills\* "$HOME\.claude\skills\"
```

Restart Claude Code. The skills show up as `/ad-cloner`, `/email-cloner`, `/seo-fixer`, `/product-scout` and `/weekly-report`.

## Use

Make a folder for your store and open Claude Code in it:

```bash
mkdir my-store && cd my-store && claude
```

Then ask in plain words:

```
/ad-cloner here are 6 ads from my competitors: [paste]
/email-cloner rebuild the welcome flow from the emails in inbox/
/seo-fixer audit https://my-store.com
/product-scout niche: travel accessories, market: US
/weekly-report
```

On the first run each skill asks a few questions about your brand and store and saves the answers to `brand.md` / `store.md`, so you answer them once. Results land in `out/`.

To run all five in parallel, ask Claude Code to start them as subagents:

```
run ad-cloner, email-cloner, seo-fixer, product-scout and weekly-report as parallel subagents
```

## What they can't do

- They don't log into your store, ad accounts or mailbox. They see public pages and the files and text you give them.
- They don't publish anything. You get drafts and paste-ready fixes, and you decide what ships.
- They don't invent numbers. Missing data is marked as missing, assumptions are marked `ASSUMED`.

## License

MIT
