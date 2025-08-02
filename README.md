# UCP‑Wiki

> **Unofficial Crusader Patch — Central Documentation Hub** > Flat Markdown pages for players, modders, and developers. Easily embeddable and readable on GitHub.

---

## What is this repo?

* A **single source of truth** that replaces the separate wikis of `UnofficialCrusaderPatch2` and `UnofficialCrusaderPatch3`.
* A comprehensive **knowledge base** for vanilla Stronghold Crusader mechanics, stats, and strategies.
* Every page lives under `docs/` as plain `.md`, so:
    * GitHub shows a nice preview out-of-the-box.
    * Other sites can load the raw Markdown via JavaScript and render it with any library (`marked`, `markdown-it`, etc.).

---

## Quick links

| Section | Page |
|---|---|
| Getting Started | [`docs/Player-Guides/Getting-Started/Recommended-Setups.md`](docs/Player-Guides/Getting-Started/Recommended-Setups.md) |
| Crusader Wiki | [`docs/Stronghold-Crusader-Wiki/Units/Units-Overview.md`](docs/Stronghold-Crusader-Wiki/Units/Units-Overview.md) |
| AI Lords Guide | [`docs/Stronghold-Crusader-Wiki/AI-Lords/AI-Lords-Overview.md`](docs/Stronghold-Crusader-Wiki/AI-Lords/AI-Lords-Overview.md) |
| Create a Mod | [`docs/Modding-with-UCP/Creating-Extensions/Creating-a-Plugin.md`](docs/Modding-with-UCP/Creating-Extensions/Creating-a-Plugin.md) |
| Developer Zone | [`docs/Developer-Zone/Contributor-Tutorial.md`](docs/Developer-Zone/Contributor-Tutorial.md) |
| Project Roadmap | [`docs/Project/Roadmap-Ideas.md`](docs/Project/Roadmap-Ideas.md) |

See the full sidebar structure in `docs/_Sidebar.md`. Note that the custom website will generate this sidebar automatically from the file structure.

---

## Embedding the wiki in your own site

To embed a page, you need its raw GitHub URL. For example, to fetch and render the `Installation.md` page:

+++js
// Example: fetch & render the Installation page
import { marked } from 'marked';

const url = 'https://raw.githubusercontent.com/UnofficialCrusaderPatch/UCP-Wiki/main/docs/Player-Guides/Getting-Started/Installation.md';

fetch(url)
  .then(r => r.text())
  .then(md => {
    document.getElementById('wiki-root').innerHTML = marked.parse(md);
  });
+++