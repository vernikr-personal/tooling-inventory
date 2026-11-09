# Repository instructions

- Keep repository content in English; reply to the user in Russian.
- Keep changes tied to a GitHub Issue and keep the inventory concise and evidence-based.
- Treat `INVENTORY.md` as the authoritative setup list. Distinguish installed, configured, tested, and blocked tools.
- Prefer free plans or explicit free quotas when evaluating alternatives. Record current limits and paid features separately.
- Use `uvx ty check` for Python type checking when Python code is present; `ty` can also be installed with `uv tool install ty`.
- Parallel MCP 2.0 endpoint: `https://mcp.parallel.ai/mcp?login`. Its free `web_search`, `web_fetch`, and `web_decisions` tools do not require an account; `web_research` requires Parallel sign-in and is billed. Use the no-login endpoint when only free tools are needed.
- TinyFish supports multi-step Deep Research through TinyResearch, which produces cited reports, and TinySet for structured datasets. TinySearch and TinyFetch remain free within published limits; TinyResearch Deep/Max reports are paid ($2/$3 per completed report) after any account credits. Research is limited to public web sources.
- OmniRush currently permits only supported local MCP servers; remote MCP endpoints such as Parallel are blocked by its runtime policy. Do not mark such a connection as active unless the product's supported-server policy changes.
- Preserve unrelated inventory entries and do not modify scheduled automations as part of repository maintenance.
