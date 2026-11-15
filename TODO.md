# TODO

## Done
- [x] Repo created and scaffolded (README, TODO, .gitignore with `research/` excluded)
- [x] Brand chosen: **HydRealestate**
- [x] REA setup dry-run reviewed (would add the `rea` MCP server to Claude Code config + install the REA skill)

## Phase 0 — Set up REA (on your own machine)
- [ ] Run `npx -y rea-agents@latest setup --client claude_code --dry-run --json`, review, then apply with `--yes`
- [ ] Restart Claude Code; confirm `list_browser_targets`, `inspect_web_page`, `capture_web_screenshot`, `observe_web_session`, `analyze_web_bundle`

## Phase 1 — Research (passive, on your own machine)
- [ ] Launch a separate Chrome profile with remote debugging (see docs/phase1-runbook.md)
- [ ] Inspect + screenshot: home, results (list + map), filters, detail, agent, agency, suburb, new development
- [ ] observe_web_session during filter / sort / paginate / list↔map
- [ ] analyze_web_bundle for route patterns and data shape only (summarise, no code)
- [ ] Write `docs/research.md` incl. AU → Hyderabad concept map; commit and push
- [ ] Review research.md before Phase 2

## Phase 2 — Plan (next, in a cloud or local session)
- [ ] Architecture, schema, route map, components, phased build plan
- [ ] Decisions: maps provider, SMS/OTP (DLT), payments, hosting region

## Phase 3 — Build MVP
## Phase 4 — Quality
