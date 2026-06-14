# Pluck

**Pull what you need from deep JSON.**

A fast, private, single-file JSON inspector for developers who live in nested API payloads.

**Live:** https://json.codeology.tech

Everything runs in your browser. The page makes **zero outbound requests after it loads** — no analytics, no font CDNs, no telemetry, nothing. Your data never leaves your machine.

## Why this exists

Most JSON viewers choke on large files, can't query, and can't answer the question you actually have: *"show me field X from every record, alongside field Y from its parent."* This tool does.

## Features

- **Virtualized tree view** — handles 100k+ node documents without freezing; deep nesting won't blow the stack
- **Three query modes**
  - **Search** — live find across keys + values, with match navigation
  - **Filter** — JavaScript expressions against your data (`data.items.filter(x => x.active)`), with 20 built-in helpers (`groupBy`, `countBy`, `sum`, `unique`, `sortBy`, `pick`, `project`, `get`, …)
  - **Path** — JSONPath subset: `$.users[*].name`, `$..id`, slices, unions, negative indices
- **Table view** — any array of objects renders as a sortable table; paginated at 2,000 rows; export to CSV (full dataset, not just the visible page)
- **Table builder** — click any nested array in the tree, tick the fields you want (including fields from ancestor levels), and the `flatMap` chain is generated and applied for you. No more hand-writing triple-nested loops
- **Lenient parsers on demand** — strict JSON by default; one click to retry as **JSONC** (comments, trailing commas) or **JSON5** (unquoted keys, single quotes, hex, …). `.jsonc` / `.json5` files auto-detect
- **Parse stringified JSON inline** — values that contain escaped JSON get a "parse →" tag; one click expands them in place, with undo
- **Saved commands** — name and store your frequent filter/path expressions, scoped per mode
- **Command palette** — `Ctrl+K` for everything
- **Atom One Dark / Light themes** — toggle in the topbar, remembered across visits
- **Format / minify / stats** — node counts, depth, byte size, type breakdown

## Privacy model

- Pasted/opened JSON is processed entirely in memory, in your browser tab
- **Session persistence is OFF by default** — close the tab and your data is gone. An explicit opt-in toggle (help panel) enables restore-on-reload via `localStorage`, on your machine only
- Saved commands and theme choice persist locally — those are explicit actions, not captured data
- A "Clear all saved data" button wipes everything
- The single HTML file *is* the entire application — audit it yourself

## A note on Filter mode

Filter expressions are evaluated as JavaScript in your browser (`new Function`). This is the same trust level as your browser's DevTools console: powerful, local, and only as safe as what you type into it. **Don't paste filter expressions from sources you don't trust.**

## Run it yourself

It's one file with no build step and no dependencies:

1. Download `index.html` (or clone this repo)
2. Open it in a browser — done

Host it anywhere that serves static files. No server-side anything required.

## Browser support

Modern evergreen browsers (Chrome/Edge, Firefox, Safari). Built for desktop; small screens get a friendly notice with a continue-anyway option.

## Support & contributions

This is a personal tool, shared as-is. Issues and PRs are welcome but responses aren't guaranteed — see the license: no warranty, no SLA, just a tool I built because I needed it.

## License

[MIT](LICENSE) — do what you like, keep the notice, don't blame me.
