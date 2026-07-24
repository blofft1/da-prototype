# Shipping the DA redesign as a real Document Authoring app

*One-pager for product + engineering. Prototype: https://blofft1.github.io/da-prototype/*

## The ask

We've prototyped a redesigned Document Authoring (DA) admin + editing experience. This
outlines what it would take to turn it from a clickable mockup into a **real DA app** that
runs against live content.

## It's a supported, low-friction path

DA is extensible by design — no forking DA itself. Two mechanisms:

- **Custom Apps/Tools** — a small web app (HTML + CSS + JS) that lives in your Edge Delivery
  GitHub repo, is registered in the site config sheet, and launches inside DA from
  `da.live/apps`. It gets the signed-in session via the **DA SDK** and reads/writes content
  through the **DA Admin APIs** (List + Source). *This is the path for our browser.*
- **Editor plugins / Library Extensions** — lighter in-editor add-ons (pickers, tag
  browsers) for enhancements inside the document editor.

## Precedent: Adobe already built ~80% of our browse view

Adobe's DevXSC team shipped **`better-da`** (in `AdobeDevXSC/drago-toolkit`) — "a content
browser for DA with Tree, Taxonomy, and Gallery views, filtering, inline metadata editing,
and a self-generating content inventory." Its filters are literally
All / Pages / Fragments / Config / Locales / Assets / Folders — the same model we designed
independently. **This de-risks the approach: the pattern is proven and in-market.**

## What we've already done

A working DA-app version of the **Content Browser** is in the prototype repo under
`/da-app/`. It uses the real DA SDK + List API when run inside DA, and falls back to sample
data for standalone preview. It's ready to drop into a site's code repo and register.

## Proposed phases

| Phase | Scope | Effort |
|---|---|---|
| **1 — Browse (live)** | Register the Content Browser app; real content via List API; open pages in the DA canvas | Small — largely done |
| **2 — Rich metadata** | Self-generating inventory sheet for Title/Status/Tags (like `better-da`); inline editing via Source API | Medium |
| **3 — Actions** | Multi-select bulk actions (publish, move, delete) and the ⋯ metadata panel wired to Source API | Medium |
| **4 — Editor & rail** | Outline / Properties enhancements as editor plugins; Fragments console | Larger — needs design + eng alignment |

## Open questions for the team

- Design system: adopt **Adobe Spectrum** (as `better-da` does) or keep our lighter styling?
- Relationship to `better-da` — extend/contribute to it, or ship our own app?
- Which site repo hosts the app, and who owns the config-sheet registration?

## References

- DA developer docs — <https://docs.da.live/developers>
- List API — <https://docs.da.live/developers/api/list>
- DA source — <https://github.com/adobe/da-live>
- `better-da` reference tool — `AdobeDevXSC/drago-toolkit`, `tools/better-da/`
