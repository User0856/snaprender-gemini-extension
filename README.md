<img src="assets/logo.png" alt="SnapRender" width="64" height="64">

# SnapRender extension for Gemini CLI

Give Gemini CLI eyes on the web. [SnapRender](https://snap-render.com) renders public web pages in a real browser, so Gemini can see a page the way a visitor does (desktop, phone, full page, dark theme) and read it as clean markdown before it writes code.

## Install

```sh
gemini extensions install https://github.com/User0856/snaprender-gemini-extension
```

Restart Gemini CLI after installing. The first time Gemini uses the SnapRender server, it opens your browser: sign in to SnapRender (or create a free account) and approve. Inside Gemini CLI, `/mcp auth snaprender` repeats the sign-in and `/mcp` shows the server and its tools.

Update later with `gemini extensions update snaprender`.

## What you get

- **The hosted SnapRender MCP server** (`https://app.snap-render.com/mcp`, Streamable HTTP, OAuth sign-in) with 11 tools: `take_screenshot`, `extract_content`, `batch_screenshots`, `get_batch_status`, `check_screenshot_cache`, `get_usage`, `sign_screenshot_url`, and `list_webhooks`, `create_webhook`, `delete_webhook`, `test_webhook`.
- **A context file** (`GEMINI.md`) that tells Gemini when to use each tool and what SnapRender cannot reach.
- **Three agent skills:**
  - `see-web-page`: screenshots a page on desktop and on a phone and reports layout problems.
  - `read-web-page`: reads a page as markdown, trimmed to the main content.
  - `watch-web-page`: sets up scheduled captures that alert when a page changes (schedules are created in the SnapRender dashboard or REST API; the MCP server creates the webhook for alerts).

Ads and cookie banners are removed from captures by default.

## No browser on this machine? Use an API key

OAuth needs a local browser, so it does not work over SSH or in containers. Create an API key in the dashboard at https://app.snap-render.com/dashboard, set it as `SNAPRENDER_API_KEY` in your shell, and add this to `~/.gemini/settings.json`. A server in `settings.json` takes precedence over the extension's server with the same name:

```json
{
  "mcpServers": {
    "snaprender": {
      "httpUrl": "https://app.snap-render.com/mcp",
      "headers": {
        "Authorization": "Bearer ${SNAPRENDER_API_KEY}"
      }
    }
  }
}
```

Or run the server locally with Node.js: `"command": "npx", "args": ["-y", "snaprender-mcp"], "env": { "SNAPRENDER_API_KEY": "${SNAPRENDER_API_KEY}" }`.

## Try it

- Screenshot https://example.com on desktop and on iPhone 15 Pro and list what looks broken on mobile
- Read the docs at https://example.com/docs as markdown and summarize the API before we write code
- How many SnapRender captures do I have left this month?

## Good to know

- **Public pages only.** SnapRender cannot reach localhost, private networks or pages behind a login, and it does not click through multi-step flows. Use a public or preview deployment URL.
- **Firewall checks.** If a capture of your own site shows a security check such as "Just a moment...", one firewall rule lets SnapRender through: https://snap-render.com/docs/allow-snaprender
- **Free plan:** 200 captures a month (25 until you verify your email), no card. Each screenshot or extraction uses one capture; failed renders are free. Paid plans: https://snap-render.com/pricing

## What it sends

The extension runs no code on your machine. When Gemini calls a SnapRender tool, the URL and capture options are sent to `https://app.snap-render.com`. SnapRender does not read your code or files. Privacy policy: https://snap-render.com/privacy

## Other clients

Claude Code, Cursor, Codex and Agent Skills (skills.sh): https://github.com/User0856/snaprender-agent-plugin. Setup guides for every client: https://snap-render.com/ai-connectors

## Links

- AI agent guide: https://snap-render.com/ai-agents
- Docs: https://snap-render.com/docs
- Support: support@snap-render.com

## License

MIT
