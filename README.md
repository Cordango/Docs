# Cordango Docs

The Cordango documentation site, live at [docs.cordango.com](https://docs.cordango.com).

Mounted as a submodule at `docs/` in the AppBuilder working repository.

## Local preview

```bash
npm i -g mint
mint dev
```

Serves the site at http://localhost:3000 and reloads on save.

```bash
mint broken-links
```

Checks every internal link resolves. Worth running before a deploy.

## Hosting

We run on Mintlify, and that was a decision rather than a default.

It got the documentation live quickly. The build, the hosting and the search are handled, deploying
is a push, and the weeks we would have spent standing up our own pipeline went into writing pages
instead. For a product whose documentation did not exist yet, shipping beat owning.

We also know it does not stay. Mintlify is a hosted US platform, and the sovereignty claim we make
elsewhere is not one we get to make loosely. So this moves. That is planned work, not a regret:
we took the fast option on purpose, with the replacement already understood.

What the move costs is mostly up to us in the meantime. New pages go in plain markdown wherever a
component is not genuinely earning its place, because every component kind adopted is one more thing
to carry across.

## Ground rules

**Document what exists.** Every command, route, header and token prefix on this site was read out of
the source. If something is planned rather than built, say so on the page, the way `mcp/` does.

**House voice.** Plain and direct, matching the CLI's own help text and the marketing site. No
em-dashes, no marketing triads, no buzzwords.

Brand colours track `marketing/style.css`: signal `#1D4ED8`, signal-2 `#3B6BF0`.

## Still to decide

- German translation. The product and the marketing site are EN and DE; `navigation.languages` in
  `docs.json` is currently empty.
- Whether the API reference stays hand-written or is generated from an app's `openapi.json`.
- A real MCP tool reference, once there is a server to document.
- Whether the CLI reference is generated from the command table so it cannot drift.

## Keeping it honest

The pages assert specifics that live in `cordango/cordango`: the command table
(`src/Cordango.Cli/Commands/Help.cs`), field types and the entity shape
(`schemas/app-definition.schema.json`), aggregate kinds (`src/Cordango.Compiler/Cord/CordAggregate.cs`),
semantic op names (`schemas/ops/*.json`), and the target ids
(`src/Cordango.Cli/Generate/Targets.cs`).

The "See it in action" trees on `concepts.mdx` assert generated filenames, from the emitters
(`src/Cordango.SourceGen.DotNetVue/Emit/`) and the scaffold (`src/Cordango.Standalone/Templates/`).
The file count beside them came from a real `cordango build` of the `expenses` example. Both drift
silently when the generator changes.

The API pages assert routes and the error envelope from the platform repository
(`AppRuntimeController`, `ApiError`, `AccessKeyAuthentication`, `DataApi`).

When any of those change, these pages are wrong and nothing will tell you.
