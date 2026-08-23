# Cordango Docs

Cordango MCP, API, and Developer Documentation — built with [Mintlify](https://mintlify.com).

## Local Development

Install the Mintlify CLI:

```bash
npm i -g mintlify
```

Start the local preview server from the root of this repository:

```bash
mintlify dev
```

Open [http://localhost:3000](http://localhost:3000) to view the docs.

## Structure

```
.
├── mint.json                  # Mintlify configuration
├── introduction.mdx           # Landing page
├── quickstart.mdx             # Quickstart guide
├── development.mdx            # Local development guide
├── mcp/
│   ├── overview.mdx           # MCP overview
│   ├── tools.mdx              # MCP tool reference
│   └── authentication.mdx    # MCP authentication
└── api-reference/
    ├── introduction.mdx       # API overview
    ├── authentication.mdx     # API authentication
    └── endpoints.mdx          # API endpoint reference
```

## Publishing

Push changes to this repository. Mintlify will automatically build and deploy the updated docs.
