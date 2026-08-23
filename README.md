# Cordango Docs

The Cordango documentation site, built with [Mintlify](https://mintlify.com).

This repository is mounted as a submodule at `docs/` in the AppBuilder working repository.

## Local preview

```bash
npm i -g mint
mint dev
```

That serves the site at http://localhost:3000 and reloads on save.

```bash
mint broken-links
```

Checks every internal link resolves. Worth running before a deploy.

## Layout

| Path | What it is |
| --- | --- |
| `docs.json` | Site config: theme, brand, navigation. The current Mintlify format; `mint.json` is the deprecated one. |
| `index.mdx`, `quickstart.mdx` | Get started. |
| `ai/` | Tuned starting prompts per agent: Claude Code, Codex, Cursor, GLM. |
| `concepts.mdx`, `concepts/` | Semantic source (YAML), the App Definition (JSON), the schema, targets, core apps. |
| `guides/` | Editing apps, semantic operations, roles, validation and CI, deploying. |
| `security.mdx` | What leaves your machine and what does not. |
| `cli/` | The `cordango` command. |
| `api-reference/` | The HTTP surface of a running app. |
| `mcp/` | Placeholder. The MCP server does not exist yet. |
| `logo-light.png`, `logo-dark.png`, `favicon.svg` | Brand assets, copied from the marketing site. |

Brand colours track `marketing/style.css`: signal `#1D4ED8`, signal-2 `#3B6BF0`.

## Ground rules

**Document what exists.** Every command, route, header and token prefix on this site was read out
of the source. If something is planned rather than built, say so on the page, the way `mcp/`
does.

**House voice.** Plain and direct, matching the CLI's own help text and the marketing site. No
em-dashes, no marketing triads, no buzzwords.

## Still to decide

- Custom domain (`docs.cordango.com`) and Mintlify deployment wiring.
- German translation. The product and marketing site are EN+DE; Mintlify supports this through
  `navigation.languages`.
- Whether the API reference stays hand-written or is generated from an app's `openapi.json`.
- A real MCP tool reference, once there is a server.
- Whether the CLI reference should be generated from `cordango help --json` so it cannot drift.

## Keeping it honest

The pages assert specifics that live in `cordango/cordango`: the command table
(`src/Cordango.Cli/Commands/Help.cs`), field types and the entity shape
(`schemas/app-definition.schema.json`), aggregate kinds (`src/Cordango.Compiler/Cord/CordAggregate.cs`),
semantic op names (`schemas/ops/*.json`), and the target id
(`src/Cordango.SourceGen.DotNetVue/DotNetVueGenerator.cs`).

The API pages assert routes and the error envelope from the platform repository
(`AppRuntimeController`, `ApiError`, `AccessKeyAuthentication`, `DataApi`).

When any of those change, these pages are wrong and nothing will tell you.
