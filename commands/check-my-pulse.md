---
description: Check how your brand shows up in AI search across Claude, ChatGPT, Perplexity, and Gemini using the kariops pulse connector.
argument-hint: "[brand name]"
---

The user wants to check their brand's visibility in AI search using the kariops pulse MCP server.

Use the kariops pulse tools (exposed by the connected `kariops-pulse` MCP server) to help. The relevant tools:

- `scan_brand_citations` returns the most recent monthly scan: citation share per engine, mention count, and total queries run.
- `get_scan_history` returns per-engine citation share across recent monthly scans, so the user can see the trend.
- `get_engine_diagnostics` explains why a specific engine is missing the brand.
- `compare_competitors` shows the brand's share side by side with tracked competitors.

Steps:

1. If the user named a brand in `$ARGUMENTS`, use it. Otherwise ask which registered brand to check.
2. Call `scan_brand_citations` for that brand and present citation share across all four engines (Claude, ChatGPT, Perplexity, Gemini) in a compact table.
3. Offer the trend view (`get_scan_history`) and, if any engine shows low or zero share, offer `get_engine_diagnostics` for that engine.
4. If the user has no key on file or no scan data, relay the connector's own error verbatim and point them to the dashboard at https://pulse.kariops.com to add keys or run a scan. Do not invent numbers.

Never claim more than four engines are scanned. Keep the output scannable, not promotional.
