# AGENTS Guide

## Project purpose

**Translucence** is a design corpus of **interconnected Bible articles**. A core goal is to present **modular arguments** about Biblical truths — reusable claims and supporting pieces that link together, rather than one-off essays.

The git-tracked corpus in `./content/` is a property graph: node markdown and relationship instances under `content/data/`, workspace model JSON under `content/model/`, with a local SQLite cache under `./data/` for fast queries.

> **Dev environment:** Open the **silentorb-workbench** devcontainer for editor, tests, and cache sync. This repo’s tasks cover content sync and validation only.

## Project context

- Keep updates aligned with the repository’s current scope and documentation.
- The `./docs` directory is primarily for AI agents. Authoritative **project feature** specs for Tome tooling live in the sibling **`tome`** repo at `../tome/docs/features/` (or `/workspaces/tome/docs/features/` from silentorb-workbench). The **design ontology** (intent; types still TBD) lives at [`docs/ontology.md`](./docs/ontology.md).
- The `./content` directory is the **canonical store root**: `content/data/nodes/{shard}/{nodeId}.md` per live node (archived under `content/archive/nodes/`); `content/data/relationships/{shard}/{digest}.json` per live relationship (archived under `content/archive/relationships/`); `content/model/` holds `associations.json`, `table-presentation.json`, `schema.json`, `table-schemas.json`, `views.json`, `dynamic-properties.json`, `extensions.json`, and `sequencing.json`.
- The `./data/tome.sqlite` file is a **local query cache** (gitignored). It is rebuilt from `./content` on editor API startup and via `bun run content:sync`.
- TypeScript domain scripts live under `./scripts/`; Tome packages live in the sibling **tome** repository. In silentorb-workbench, use the **`tome` Compose service** for `editor:dev` (not this repo directly). The editor defaults to Marloth; point `TOME_CONTENT_PATH` / `TOME_DB_PATH` at this repo to edit Translucence in the editor.
- All external dependencies and tooling installs should be performed within the silentorb-workbench devcontainer. **Rebuild the container** after changing `package.json` or `bun.lock` in workbench or tome — do not run `bun install` manually in a terminal or on the host.

## Terminology

| Term | Meaning |
| ---- | ------- |
| **Project feature** | A workspace capability documented in the sibling **`tome`** repo under `docs/features/` (e.g. tome-db, tome-editor). Use this phrase when discussing tooling or agent specs—not graph nodes. |
| **Node** | Any entity in the design graph (SQLite `nodes` table). |
| **Relationship** | A link between two nodes with a **relationship type** and properties. One JSON file per edge under `content/data/relationships/` (archive under `content/archive/relationships/`); SQLite cache expands to directed projections. |
| **Page** | UI representation of a node in the editor (`NodePageView`, page title, sections, `getNodePageDetail`). Not the same as a raw export file. |
| **Schema** | Git-tracked relationship rules in `content/model/schema.json`. Not SQLite DDL. |
| **Type table** | Any node used as an `IS_A` target and/or declared in `content/model/table-schemas.json`. |

## Graph data workflow

The `./content/` tree is **authoritative and git-tracked**. Edit content files (or use tooling that writes them). `TOME_CONTENT_PATH` points at the **content root** (`./content`), not `content/data`.

| Task | Do | Do not |
| ---- | -- | ------ |
| Add or edit nodes, bodies, titles | Edit `content/data/nodes/{shard}/{nodeId}.md` (or `content/archive/nodes/…`) or use the Tome editor / `ContentStore` (`tome-flatfile` / `tome-db` in sibling **tome** repo) | Edit `data/tome.sqlite` directly |
| Add or edit relationships | Edit `content/data/relationships/**/*.json` (or `content/archive/relationships/…`), `content/model/associations.json`, or use editor / `ContentStore` mutation APIs | Duplicate relationships in node markdown files |
| Dynamic property bindings | Edit `content/model/dynamic-properties.json` | Use removed `dynamic_`* SQLite overlay tables |
| Extension registration | Edit `content/model/extensions.json` | Hard-code extension modules in tome-editor |
| Table view tabs (custom / generated) | Edit `content/model/views.json` or use editor tab CRUD | Rely on removed per-node view frontmatter |
| Refresh local cache | `bun run content:sync` or start `editor:api` (rebuilds cache + watches `./content`) | Commit `data/tome.sqlite` |

See the sibling **tome** repo [`docs/features/tome-db.md`](../tome/docs/features/tome-db.md) for file formats and API.

## Working conventions

- Make focused changes that address the requested task only.
- Avoid unrelated refactors unless they are required to complete the task safely.
- Prefer small, incremental edits that are easy to review.
- **Prototypal stage — no backwards compatibility.** Delete old shapes; migrate content in the same change.
- **Script language:** agentic scripts should use **TypeScript** (Bun) by default. One-off throwaway scripts may still be written in Python.

## Implementation expectations

- Read existing files before editing to preserve intent and style.
- Keep assumptions explicit in commit or PR notes when behavior is unclear.
- Run relevant checks or tests when changing code, if such checks are available.
- Add self-documentation under `./docs` when making agent-relevant updates.

## Feature documentation

Authoritative design specs for **project features** live in the sibling **`tome`** repo (`../tome/docs/features/`).

**Do not read all feature docs by default.** When your task matches a row, read only that file. Treat the feature doc as the source of truth over implementation when they disagree—update code or the doc explicitly.

For **design data** (what nodes mean, how they relate conceptually), read [`docs/ontology.md`](./docs/ontology.md) **in addition to** schema-specific docs below.

| If your task involves… | Read |
| ---------------------- | ---- |
| Design domain model, node types, relationships | [`docs/ontology.md`](./docs/ontology.md) |
| SQLite property graph, `data/tome.sqlite`, `tome-db` | [`../tome/docs/features/tome-db.md`](../tome/docs/features/tome-db.md) (+ ontology when interpreting data) |
| Sets (`set` trait, type tables, archive hub) | [`../tome/docs/features/sets.md`](../tome/docs/features/sets.md) |
| Web markdown editor, `tome-editor` | [`../tome/docs/features/tome-editor.md`](../tome/docs/features/tome-editor.md) |
| Tome HTTP / editor API shape (use-case endpoints) | [`../tome/docs/features/web-api-design.md`](../tome/docs/features/web-api-design.md) |
| Graph Explorer, LOD layers, anchor-scoped graph viz | [`../tome/docs/features/graph-explorer.md`](../tome/docs/features/graph-explorer.md) |
| Editing article/argument content in the graph | [`docs/ontology.md`](./docs/ontology.md) + [`../tome/docs/features/tome-db.md`](../tome/docs/features/tome-db.md) |
| Table presentation: scope tabs, row groups, drag-and-drop reorder | [`../tome/docs/features/table-presentation.md`](../tome/docs/features/table-presentation.md) |
| Dynamic properties, computed columns | [`../tome/docs/features/dynamic-properties.md`](../tome/docs/features/dynamic-properties.md) |
| Table view tabs, `views.json` | [`../tome/docs/features/views.md`](../tome/docs/features/views.md) |
| Type table columns, `table-schemas.json` | [`../tome/docs/features/table-schemas.md`](../tome/docs/features/table-schemas.md) |
| Static website generation (Astro) | [`../tome/docs/features/static-website.md`](../tome/docs/features/static-website.md) |
| Extension system (runtime-loaded packages, page blocks) | [`../tome/docs/features/extensions.md`](../tome/docs/features/extensions.md) |
