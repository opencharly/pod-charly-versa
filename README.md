# pod-charly-versa

The `charly-versa` candy of the OpenCharly candy library, as a standalone repo
(the candy de-submodule cutover, kind-prefixed naming). It is a **metadata
concept candy**: it ships no install content of its own and exists to own the
`skill:` entities for the versa family whose names have no namesake candy.

## What it provides

| `charly.yml` node | Kind | `name:` | Projected as |
|---|---|---|---|
| `charly-versa` | `candy` | — | the concept candy (validate-satisfying no-op plan) |
| `airflow-layer-skill` | `skill` | `airflow-layer` | `/charly-versa:airflow-layer` |
| `debug-tools-layer-skill` | `skill` | `debug-tools-layer` | `/charly-versa:debug-tools-layer` |
| `maputnik-layer-skill` | `skill` | `maputnik-layer` | `/charly-versa:maputnik-layer` |
| `marimo-layer-skill` | `skill` | `marimo-layer` | `/charly-versa:marimo-layer` |
| `marimo-mcp-skill` | `skill` | `marimo-mcp` | `/charly-versa:marimo-mcp` |
| `osm-tools-layer-skill` | `skill` | `osm-tools-layer` | `/charly-versa:osm-tools-layer` |
| `sway-browser-ecovoyage-skill` | `skill` | `sway-browser-ecovoyage` | `/charly-versa:sway-browser-ecovoyage` |

The seven skills document the versa image's component layers: the marimo reactive
notebook + MCP server, the Apache Airflow 3.x layer, the OSM tooling + martin
vector-tile server, the Maputnik style editor, the debug-toolkit layer, the
marimo MCP tool catalog, and the `sway-browser-ecovoyage` chrome-devtools-mcp
debug bed.

## How it is consumed

`candy/plugin-marketplace` regenerates the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus from
these entities:

```bash
charly marketplace generate --root <marketplace-checkout> --out <marketplace-checkout>
```

The generated `versa/skills/*/SKILL.md` files carry a DO-NOT-EDIT banner — edit
the `skill:` entity here and regenerate; never the projected file.

## Layout

- `charly.yml` — the `charly-versa` candy entity plus the seven `skill:` entities.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — this user overview.

## Related

- Owning procedure: `/charly-internals:skills` — when and how to update a skill
  entity and regenerate the corpus.
- The versa image itself is documented by `/charly-versa:versa` — the family
  skill resolved in the marketplace corpus at `versa/skills/versa/SKILL.md`
  (the `/charly-versa:` prefix is the marketplace family `versa`, i.e. the
  `charly-versa` plugin; the `versa` skill in it is owned by the
  `distro-cachyos` repo's `cachyos-app-skills` candy, not by this repo).
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
