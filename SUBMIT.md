# Listing this extension

## Gemini CLI extension gallery (geminicli.com/extensions)

No form. The gallery crawler lists public repositories automatically once a day when:

1. the repository is public on GitHub (done),
2. it has the GitHub topic `gemini-cli-extension` (done),
3. `gemini-extension.json` sits at the repository root (done),
4. the repository is tagged (done: `v1.0.0`, with a GitHub release).

If the extension is not on https://geminicli.com/extensions/browse/ after 24 to 48 hours, GitHub code search may not have indexed `gemini-extension.json` yet; wait another day before changing anything. For a new version, raise `version` in `gemini-extension.json`, push, and tag (`v1.0.1`).

## Cursor, Claude plugin directory, Codex

Those portals take the other repository, https://github.com/User0856/snaprender-agent-plugin. The exact portal URLs, fields and text to paste are in its SUBMIT.md:

- Cursor Marketplace: https://cursor.com/marketplace/publish
- Claude plugin directory: https://claude.ai/directory/manage (Submit new, Plugin bundle)
- OpenAI plugin portal (Codex): OpenAI Platform, Plugins, ZIP upload (guide https://developers.openai.com/plugins/deploy/submission)
