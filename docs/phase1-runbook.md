# Phase 1 runbook — REA research on your own machine

Do this phase in Claude Code on your own computer. REA has to attach to the Chrome
you are browsing in, and a cloud session can't reach your machine's loopback.

## Ground rules

- Passive observation only. You browse by hand; REA inspects what is already open.
- No scraping, no automated crawling, no bypassing bot protection. If a page shows a
  challenge or block, stop and note it in research.md.
- Study structure, flows, filter model, URL patterns and data shape. Do not copy code,
  CSS, markup, images, icons, logo, colours, fonts, wording or listing data.
- Screenshots and raw captures go in `research/` (gitignored). Only `docs/research.md`
  is committed.

## 1. Clone and set up REA

```bash
git clone https://github.com/mavsworld26/HydRealestate.git && cd HydRealestate
```

```bash
npx -y rea-agents@latest setup --client claude_code --dry-run --json
```

Review the plan. In this session's dry run it would (a) add a `rea` MCP server to your
Claude Code config, with a backup, and (b) install the REA skill. Then apply it:

```bash
npx -y rea-agents@latest setup --client claude_code --yes
```

Restart Claude Code. Confirm these tools are listed: `list_browser_targets`,
`inspect_web_page`, `capture_web_screenshot`, `observe_web_session`, `analyze_web_bundle`.

## 2. Launch a separate Chrome profile with remote debugging

Chrome 136+ ignores `--remote-debugging-port` on the default profile, so use a
throwaway `--user-data-dir`. Don't sign in to any accounts in this profile. While
the debugging port is open, any local process can control this browser.

macOS:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --remote-debugging-port=9222 --remote-debugging-address=127.0.0.1 --user-data-dir="$HOME/.rea-browser-profile" https://www.realestate.com.au/
```

Linux:

```bash
google-chrome --remote-debugging-port=9222 --remote-debugging-address=127.0.0.1 --user-data-dir=/tmp/rea-browser-profile https://www.realestate.com.au/
```

Windows (PowerShell):

```powershell
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=9222 --remote-debugging-address=127.0.0.1 --user-data-dir="$env:TEMP\rea-browser-profile" https://www.realestate.com.au/
```

Close this browser when you finish.

## 3. Prompt to paste into local Claude Code

> We're in the HydRealestate repo. Do Phase 1 research with REA, passive observation
> only. Chrome is running with remote debugging on 127.0.0.1:9222. For each page type
> I open (home; search results list view; map view; filters panel; property detail;
> agent profile; agency profile; suburb profile; new development page), wait for me
> to say it's open. Then run list_browser_targets → inspect_web_page and
> capture_web_screenshot, saving captures under research/. While I filter, sort,
> paginate and switch list↔map, run observe_web_session and record how URLs and
> navigation change. Use analyze_web_bundle only for route patterns and the general
> shape of requested data. Summarise, never reproduce code. Don't scrape, crawl or
> bypass bot protection: if blocked, stop and tell me. Then write docs/research.md
> with: page inventory, user flows, component list, search/filter model, URL scheme,
> inferred data model, SEO patterns, and an Australia → Hyderabad concept map
> (suburb → locality, agency → broker/builder, etc.). Label each finding as observed
> (REA), derived, or inferred. Commit only docs/research.md and push.

## 4. Hand back

Once `docs/research.md` is pushed, return to the cloud session (or carry on locally)
for Phase 2 planning.
