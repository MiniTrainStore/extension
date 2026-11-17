# AGENTS.md

Browser extension of Mini Train Store (minitrainstore.fr), a French model railway shop: it reads
the seller's listings on leboncoin.fr to import them into the shop. Built with
[WXT](https://wxt.dev), Vue 3, Tailwind CSS and shadcn-vue. Part of the
[espace-de-travail](https://github.com/MiniTrainStore/espace-de-travail) of the MiniTrainStore
organization.

The extension was written for the former Odoo shop (`utilities/odoo.ts`). The shop now runs on
Vendure (repository `boutique`), whose Admin API and MCP server replace the Odoo calls; the
Leboncoin synchronisation is planned there (`boutique/docs/conception/09-leboncoin.md`). Check that
document before extending the Odoo code.

## Layout

| Path | Role |
| --- | --- |
| `entrypoints/` | WXT entry points: background, content scripts (buttons injected on Leboncoin pages), popup, side panel, main page |
| `components/` | Vue components; `components/ui/` holds shadcn-vue primitives |
| `utilities/` | Parsing of Leboncoin pages (`product/`, `profile/`), categories, tags, weights, settings, Odoo client |
| `stores/` | Extension storage |

## Commands

| Command | Does |
| --- | --- |
| `npm install` | Installs the dependencies (runs `wxt prepare`) |
| `npm run dev` / `npm run dev:firefox` | Development build with live reload in Chrome / Firefox |
| `npm run build`, `npm run zip` | Production build and store package |
| `npm run compile` | Type check (`vue-tsc`) |
| `npm run lint` | ESLint |

## Rules

- Never store or log Leboncoin session cookies, API keys or personal data of buyers.
- The interface is in French, with correct accents; never use the em dash (the long dash).
- Commit directly on `main`, with Conventional Commits messages in English. Do not mention AI
  tools or assistants, and add no `Co-Authored-By` or "Generated with" lines.
