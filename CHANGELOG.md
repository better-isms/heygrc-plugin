# Changelog

## 0.1.2

- Gemini CLI extension: `gemini-extension.json` + `GEMINI.md` context (install via
  `gemini extensions install https://github.com/better-isms/heygrc-plugin`).
- Copilot custom-agent reference file: `.github/agents/heygrc-compliance-review.agent.md`.
- Per-harness install attribution: the skill now sends the `?via=` parameter matching the running
  tool (claude-plugin, codex-cli, cursor, copilot-cli, gemini-cli, agent-plugin) instead of a single
  hardcoded value.
- Keyword and description parity across all manifests (DORA, NIS 2).
- README: Gemini install command, live listing links.

## 0.1.1

- Portable Agent Plugin manifest at repo root (`plugin.json`, Agent Plugins 1.0).
- Codex CLI marketplace (`.codex-plugin/plugin.json`, `.agents/plugins/marketplace.json`).
- Cursor plugin manifest (`.cursor-plugin/plugin.json`).
- README install commands for Claude Code, Cursor, Codex, Copilot CLI, and `npx skills add`.

## 0.1.0

- Initial release. Self-hosted Claude Code plugin marketplace for heyGRC.
- `heygrc` plugin with the `/heygrc:review` setup-and-review skill.
- Bridges to the heyGRC GitHub App: install, configure company profile and frameworks as code, choose
  review cadence.
