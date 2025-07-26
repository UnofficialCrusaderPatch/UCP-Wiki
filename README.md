# UCP‑Wiki

> **Unofficial Crusader Patch — Central Documentation Hub**  
> Flat Markdown pages for players, modders, and developers.  
> Easily embeddable (via `raw.githubusercontent.com`) *and* readable on GitHub.

---

## What is this repo?

* A **single source of truth** that replaces the separate wikis of  
  `UnofficialCrusaderPatch2` and `UnofficialCrusaderPatch3`.
* Every page lives under `docs/` as plain `.md`, so:
  * GitHub shows a nice preview out‑of‑the‑box.  
  * Other sites (e.g. <https://unofficialcrusaderpatch.github.io/ucp-website-test/>) can load the raw Markdown
    via JavaScript and render it with any library (`marked`, `markdown‑it`, etc.).

---

## Quick links

| Section | Page |
|---------|------|
| Getting started | [`docs/Installation.md`](docs/Installation.md) |
| Command‑line flags | [`docs/Command-Line.md`](docs/Command-Line.md) |
| Modding – Extensions | [`docs/Extensions.md`](docs/Extensions.md) |
| AI & Balance | [`docs/AI-Character.md`](docs/AI-Character.md) |
| Developer framework | [`docs/Framework.md`](docs/Framework.md) |
| Roadmap ideas | [`docs/Roadmap-Ideas.md`](docs/Roadmap-Ideas.md) |

See the full sidebar in [`docs/_Sidebar.md`](docs/_Sidebar.md).

---

## Embedding the wiki in your own site

```js
// Example: fetch & render the Installation page
import { marked } from 'marked';

const url =
  'https://raw.githubusercontent.com/UnofficialCrusaderPatch/UCP-Wiki/main/docs/Installation.md';

fetch(url)
  .then(r => r.text())
  .then(md => {
    document.getElementById('wiki-root').innerHTML = marked.parse(md);
  });
