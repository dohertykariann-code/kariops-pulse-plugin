---
description: Draft page-copy fixes for the visibility gaps in your latest kariops pulse scan.
argument-hint: "[brand name]"
---

The user wants page-copy fix drafts for the gaps in their most recent kariops pulse scan.

Use the `draft_visibility_fixes` tool from the connected `kariops-pulse` MCP server.

Steps:

1. If the user named a brand in `$ARGUMENTS`, use it. Otherwise ask which registered brand to draft fixes for.
2. Call `draft_visibility_fixes` for that brand. The tool analyzes which queries lost visibility in the latest scan and returns specific page-copy suggestions tied to each gap.
3. Present the drafts as text the user can review and edit. Make clear these are suggestions to apply on their own site in their own editor. The connector never touches their site.
4. If there is no scan data or no key on file, relay the connector's own error verbatim and point them to https://pulse.kariops.com. Do not fabricate suggestions.

Keep the drafts practical and specific to the returned gaps. No hype.
