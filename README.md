# Translucence

A Tome design corpus of **interconnected Bible articles**. The aim is to present **modular arguments** about Biblical truths — reusable claims and supporting pieces that link together, rather than one-off essays.

Canonical graph data lives in `content/`. The local SQLite cache is `data/tome.sqlite` (gitignored).

## Development

Open [silentorb-workbench](https://github.com/silentorb/silentorb-workbench) as a sibling of this repo. Compose bind-mounts `../translucence` at `/workspaces/translucence`.

From the workbench:

```bash
bash scripts/translucence-content-sync.sh
```

VS Code task: **Translucence: sync content cache**.

The Tome editor defaults to Marloth. To point it at this corpus, override `TOME_CONTENT_PATH` / `TOME_DB_PATH` when opening the devcontainer:

```
TOME_CONTENT_PATH=/workspaces/translucence/content
TOME_DB_PATH=/workspaces/translucence/data/tome.sqlite
```

See [`AGENTS.md`](./AGENTS.md) and [`docs/ontology.md`](./docs/ontology.md).
