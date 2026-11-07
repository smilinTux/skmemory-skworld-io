# skmemory.skworld.io

Source for the public SKMemory site: **https://skmemory.skworld.io**, deployed by GitHub Pages from `main`.

SKMemory itself lives at [github.com/smilinTux/skmemory](https://github.com/smilinTux/skmemory): per-agent memory for the SK stack, with flat JSON files as the source of truth and exactly two storage tiers (a local SQLite index with an FTS5 arm, and a shared skmem-pg Postgres with pgvector, pg_search BM25 and Apache AGE).

## What is here

| Path | What it is |
|------|------------|
| `index.html`, `style.css` | The landing page: architecture, storage tiers, emotional memory, song memories, sacred barriers, connections, node setup |
| `docs.html` | Docs viewer that renders the skmemory repo's markdown live (`docs-manifest.json` is its fallback index, refreshed by a workflow) |
| `docs/` | Short static docs: getting started, memory layers, MCP server |
| `diagrams/skmemory.architecture.json` | Archify source for the component map; `diagrams/*.html` is generated from it by the `archify` workflow (CI fails a PR whose HTML is stale) |
| `og.html`, `og.png` | Social preview card source and its 1200x630 render |
| `llms.txt`, `sitemap.xml`, `robots.txt` | Crawler and LLM entry points |

## Rules for edits

- Every claim must be checkable against skmemory `main`: name the file or function that backs it. No marketing filler.
- Public site: no host names, IP addresses, private node names or private memory counts.
- No em or en dashes in site text.
- After changing `og.html`, re-render `og.png`:
  `google-chrome --headless=new --hide-scrollbars --window-size=1200,630 --screenshot=og.png file://$PWD/og.html`

## License

GPL-3.0
