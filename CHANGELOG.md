# Changelog

## 0.2.0

- New `setup` skill, preview until the context API is enabled for your organization (`/heygrc:setup`, or "set up heyGRC context"): your agent reads your Probo
  organization through its MCP server (read-only tool allowlist, published document versions only)
  and any Google Drive files you name, maps policies, controls, vendors, risks and data inventory to
  heyGRC context objects, shows a manifest, and pushes to `PUT /v1/context` only after you say yes.
  SECRET documents are never sent; signatures, approvals and people fields are always excluded.
  Removals found by a re-run are held for approval, never applied automatically. Re-running the
  skill is the sync.
- `skills/setup/context-batch.schema.json`: JSON Schema and examples for the context API body.
- Manifest and marketplace versions aligned at 0.2.0.
- `setup` fixes from a real Probo dogfood (2026-09-29): Probo cloud EU is `https://eu.probo.com`
  (the old console host no longer accepts MCP calls); a configurable self-hosted Probo base URL
  (`PROBO_BASE_URL`); a plain stop message with the one fix when a Probo key sees no organization;
  the manifest now opens with the policy-type drafts it excludes, by title, so you can publish
  them; `personal_data_category` lists split on semicolons and line breaks (commas only when there is
  neither), never inside parentheses;
  control and risk titles no longer repeat the reference; honest compile time with a progress
  check via `GET /v1/context/summary`. Mapping version is now `+m2`: every object reports updated once;
  unchanged documents reuse their compiled rules with no model cost.

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
