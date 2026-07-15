---
topic: kariops-pulse-claude-code-plugin
tier: standard
date: 2026-07-15
surfaces: [external_api, customer_facing_copy]
llm_funding: none_new
scaffolds_wired: [claude_plugin_validate]
decisions:
  location: dedicated repo kariops-pulse-plugin (not inside the Next.js server repo, so validate does not scan the whole app)
  auth: native OAuth 2.1 discovery via server .well-known endpoints (401 advertises RFC 9728 resource_metadata pointer); no pasted token, no userConfig secret
  mcp_transport: type http, url https://pulse.kariops.com/api/mcp (remote Streamable HTTP confirmed supported in plugins)
  payload: manifest + .mcp.json + two slash commands (check-my-pulse, draft-visibility-fix); no new server code
  submission: solo path platform.claude.com/plugins/submit (no org-plan gate); community marketplace anthropics/claude-plugins-community
  license: Apache-2.0 (matches server repo)
  version: pinned 1.0.0
---

# Prebuild manifest: kariops-pulse Claude Code plugin

## Output artifact + trigger
A Claude Code plugin listed in the community marketplace. Trigger: user runs `/plugin install kariops-pulse` or adds the marketplace, then `/kariops-pulse:check-my-pulse`.

## Cousin pattern (COLLAPSE to port)
This is a port to Anthropic's documented plugin format, not a fresh build. Authoritative schema pulled live via the Claude Code specialist (plugin.json, marketplace.json, .mcp.json, command frontmatter). The kariops-pulse server, its OAuth, and its nine tools already exist and are live (in production + MCP Registry). The plugin only packages a pointer + UX wrapper.

## Surfaces
- External API: the remote MCP server (already production, BYOK enforced 4 layers).
- Customer-facing copy: the plugin description, README, and command copy. Brand constraints apply (no hype, never "5 engines", never criticize, BYOK framing).
- No new LLM-funding surface: the plugin adds no server route; all engine calls stay BYOK on the existing server.

## Failure-mode catalog (pre-mortem)
1. Plugin references a token the user does not have. Mitigation: rely on native OAuth discovery, no pasted token. (Resolved in design.)
2. `validate` scans the whole Next.js app. Mitigation: dedicated repo. (Resolved.)
3. Copy drifts to "5 engines" or promotional tone. Mitigation: README + commands say four engines, non-promotional; grep before commit.
4. Remote MCP not supported in plugins. Mitigation: verified supported (type http). (Resolved.)
5. Submission requires an org plan. Mitigation: solo Console path confirmed open. (Resolved.)

## HITL checkpoints
- Human runs the submission form at platform.claude.com/plugins/submit (cannot be automated).
- Human authorizes OAuth on first `/mcp` use.

## Scope clarity (what is NOT in v1)
No new tools, no write actions, no server changes, no hooks/agents/output-styles. Two commands only. draft-visibility-fix is included (was "optional") because it is one file and mirrors a core tool.
