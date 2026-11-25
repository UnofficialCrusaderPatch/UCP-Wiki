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
| Getting Started | [`docs/User-Guides/Getting-Started/Recommended-Setups.md`](docs/User-Guides/Getting-Started/Recommended-Setups.md) |
| Crusader Wiki | [`docs/Stronghold-Crusader-Wiki/Units.md`](docs/Stronghold-Crusader-Wiki/Units.md) |
| AI Lords Guide | [`docs/Stronghold-Crusader-Wiki/AI-Lords.md`](docs/Stronghold-Crusader-Wiki/AI-Lords.md) |
| Create a Mod | [`docs/Modding-with-UCP/Creating-Extensions/Creating-a-Plugin.md`](docs/Modding-with-UCP/Creating-Extensions/Creating-a-Plugin.md) |
| Developer Zone | [`docs/Developer-Zone.md`](docs/Developer-Zone.md) |
| Project Roadmap | [`docs/Project.md`](docs/Project.md) |

The custom website generates the sidebar automatically from the file structure.

---

## Embedding the wiki in your own site

To embed a page, you need its raw GitHub URL. For example, to fetch and render the `Installation.md` page:

```js
// Example: fetch & render the Installation page
import { marked } from 'marked';

const url = 'https://raw.githubusercontent.com/UnofficialCrusaderPatch/UCP-Wiki/main/docs/User-Guides/Getting-Started/Installation.md';

fetch(url)
  .then(r => r.text())
  .then(md => {
    document.getElementById('wiki-root').innerHTML = marked.parse(md);
  });
```