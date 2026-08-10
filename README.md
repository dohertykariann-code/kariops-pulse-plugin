# Kariops Pulse (Claude Code plugin)

Track how your brand shows up in AI search across Claude, ChatGPT, Perplexity, and Gemini, straight from Claude Code. Runs monthly citation scans, compares competitors, and drafts page-copy fixes for the gaps.

This plugin is a thin wrapper over the **kariops pulse** remote MCP server (`https://pulse.kariops.com/api/mcp`). All logic runs on the server; the plugin ships two slash commands and the connection config.

## What you get

- `/kariops-pulse:check-my-pulse [brand]` guides a citation-visibility check across all four engines.
- `/kariops-pulse:draft-visibility-fix [brand]` drafts page-copy fixes for your latest scan's gaps.
- Direct access to the nine kariops pulse tools once the server is connected.

## Install

```
/plugin marketplace add dohertykariann-code/kariops-pulse-plugin
/plugin install kariops-pulse@kariops
```

On first use, run `/mcp` and authorize the `kariops-pulse` server. Claude Code walks you through the OAuth 2.1 sign-in (the same account you use at https://pulse.kariops.com). No token to paste.

**Running Claude Code over SSH or in a container?** The browser sign-in hands back to a local address on the machine running Claude Code, so a browser on a different machine can't complete it. Use the no-browser flow instead. Claude Code prints a URL, you open it in any browser, sign in, and paste the full address bar back at the prompt:

```
claude mcp login kariops-pulse --no-browser
```

Requires Claude Code v2.1.191 or newer.

## Bring your own keys

Kariops pulse is BYOK. You add your own engine API keys at https://pulse.kariops.com, encrypted at rest, and the scan cost stays yours. Kariops never spends its own money on your scans, and your keys never pass through Claude tool input or output.

## Engines scanned

Four: Claude, ChatGPT, Perplexity, and Gemini.

## Why the scan asks buyer questions, not brand searches

Nobody searches for your brand by name when they are shopping. If someone needs a caterer, they search for the best caterers with gluten-free options in their area. If they need accounting software, they search for something that works with their payroll system.

The scans are designed to simulate that. Buyer-context questions, the kind a real person types when they are actually trying to solve a problem, surface very different results than generic category queries. A brand can be invisible under "best CRM tools" and rank first under "CRM for teams that handle confidential client records."

Absence under a well-formed buyer question is the signal worth tracking. That is the gap that costs you business.

All four engines run with live search enabled, not model memory.

## Links

- Product: https://pulse.kariops.com
- Privacy: https://pulse.kariops.com/privacy
- Support: kari@kariops.com

## License

Apache-2.0
