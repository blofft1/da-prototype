# WKND Advanced — Feature Lab Book

A hands-on walkthrough to exercise the Document Authoring / Edge Delivery features on **blofft1 / wknd-advanced**, modeled on the bbird demo library (`demo.bbird.live/demo-docs/usecases`). Work top to bottom; each lab is self-contained.

## Your environment
| What | URL |
|---|---|
| DA content browser | `https://da.live/#/blofft1/wknd-advanced` |
| DA editor (canvas) | `https://da.live/canvas#/blofft1/wknd-advanced/<page>` |
| Config sheets | `https://da.live/config#/blofft1/wknd-advanced` |
| DA Apps | `https://da.live/apps#/blofft1/wknd-advanced` |
| Preview host | `https://main--wknd-advanced--blofft1.aem.page/` |
| Live host | `https://main--wknd-advanced--blofft1.aem.live/` |

**How publish works in DA:** open a page in the editor → click the **paper-plane (send) icon** → **Preview** (staging) → **Publish** (live).

---

## Part 0 — Preflight (do this once)

Confirm each item; check the box. If any fail, note it and we'll fix before continuing.

- [ ] You can open `https://da.live/#/blofft1/wknd-advanced` and see the content tree.
- [ ] You can open a page in the editor (click any page) and it loads the canvas.
- [ ] You can Preview and Publish a page (paper-plane → Preview → Publish).
- [ ] `https://da.live/apps#/blofft1/wknd-advanced` lists your apps (Content Browser, etc.).
- [ ] The Library opens in the editor (block/fragment insert menu is available).
- [ ] `https://main--wknd-advanced--blofft1.aem.live/query-index.json` returns JSON (search index — it does: 157 pages).

---

## Part 1 — Authoring basics

### Lab 1 — Orient in Document Authoring
**Goal:** Get comfortable with the DA content browser and editor.
1. Open `https://da.live/#/blofft1/wknd-advanced`.
2. Browse the tree: note `index`, `about-us`, `articles/`, `de/`, `fragments/`, `config/`.
3. Click **about-us** → it opens in the canvas editor.
4. Identify: the content area (center), the Library/insert control, and the paper-plane publish menu.
**Expected:** You can navigate content and open the editor.
**Ref:** `/demo-docs/usecases/how-to-use-document-authoring`

### Lab 2 — Build a new page
**Goal:** Author and publish a brand-new page.
1. In the content browser, go into a folder (e.g. `articles/`).
2. Click **+ / New** → **Document**; name it `lab-hello`.
3. Open it; type an **H1** ("Hello WKND"), a paragraph, and insert a **Hero** block from the Library.
4. Paper-plane → **Preview**, then open `…aem.page/articles/lab-hello`.
5. Paper-plane → **Publish**; confirm on `…aem.live/articles/lab-hello`.
**Expected:** A new page rendered on preview and live.
**Ref:** `/demo-docs/usecases/how-to-build-new-page`

### Lab 3 — Author with an Article template
**Goal:** Create a page from a template so structure/metadata are pre-set.
1. **Verify:** confirm a `templates` entry exists (Config sheets → `templates`, or a `/templates` folder).
2. New page → choose the **Article** template.
3. Fill the pre-built blocks (hero, body, metadata); Preview + Publish.
**Expected:** Page inherits the article layout and metadata automatically.
**Ref:** `/demo-docs/usecases/how-to-article-template`

### Lab 4 — Edit common elements (nav & footer)
**Goal:** Change a site-wide element once and see it everywhere.
1. Open **`/nav`** (and **`/footer`**) in the editor.
2. Edit a link/label; Preview + Publish.
3. Load any page and confirm the header/footer updated site-wide.
**Expected:** One edit propagates across all pages.
**Ref:** `/demo-docs/usecases/how-to-edit-common-elements-nav-footer`

### Lab 5 — Author a search page
**Goal:** Stand up a working search experience.
1. New page `lab-search`.
2. Insert the **Search** block from the Library.
3. Publish; open the page and search — results come from `query-index.json`.
**Expected:** Live client-side search over the site's indexed pages.
**Ref:** `/demo-docs/usecases/how-to-author-search-page`

### Lab 6 — Use the Fragment Picker
**Goal:** Reuse a shared fragment on a page.
1. Open `lab-hello`.
2. Insert a **Fragment** block; use the **Fragment Picker** to point it at `/fragments/related-articles` (or another fragment).
3. Preview — the fragment content renders inline.
**Expected:** Shared content composed into a page via reference.
**Ref:** `/demo-docs/usecases/how-to-use-fragment-picker`

### Lab 7 — Reuse structured content
**Goal:** Author schema-driven content and reuse it across pages/channels.
1. Open a structured source (a fragment or a sheet-backed block).
2. Reference it from two different pages.
3. Edit the source once; confirm both consumers update.
**Expected:** Single source of truth, multiple surfaces.
**Ref:** `/demo-docs/usecases/how-to-reuse-structured-content`

### Lab 8 — Add JSON-LD structured data
**Goal:** Emit LD+JSON so pages are machine-readable (SEO/LLM).
1. On a page, set the metadata/type that `scripts/schema.js` maps to LD+JSON.
2. Publish; open the page and **View Source** → find the `<script type="application/ld+json">` block.
3. Validate it in Google's Rich Results test.
**Expected:** Valid structured data in the page head.
**Ref:** `/demo-docs/usecases/how-to-json-ld-structured-data`

---

## Part 2 — Forms & gated content

> ⚠️ **Depends on Cloudflare Workers.** The block/worker *code* is in the repo (inherited from the bbird fork), but worker **deployment was skipped** for the first WKND demo. Until the `auth` and `contact_us` workers are deployed for wknd-advanced, run Labs 9–11 against the **live bbird site** (`demo.bbird.live`) instead, or deploy the workers first (needs dev help).

### Lab 9 — Add a form
**Goal:** Capture a submission through the EDS form pipeline.
1. New page `lab-contact`; insert the **Form** block (or reference the `contact-us` fragment).
2. Publish; submit the form on the live page.
3. Confirm handling via the `contact_us` worker (thank-you redirect / stored submission).
**Expected:** A working form submission end-to-end.
**Ref:** `/demo-docs/usecases/how-to-forms`

### Lab 10 — Login flow
**Goal:** Show sign-in on the site.
1. **Verify:** the `auth` worker + identity config are connected.
2. Add/locate the **auth-toggle** on a page; Publish.
3. Click **Sign in** and complete the flow; confirm the signed-in state.
**Expected:** Visible authenticated state.
**Ref:** `/demo-docs/usecases/how-to-showcase-login-flow`

### Lab 11 — Gated content
**Goal:** Restrict a section to signed-in users.
1. Mark a page/section as gated (per the auth pattern).
2. Publish; view signed-out (teaser/locked) vs signed-in (full content).
**Expected:** Content gated by auth state.
**Ref:** `/demo-docs/usecases/how-to-gated-content-experience`

---

## Part 3 — Governance & DA apps  *(⚙️ = verify the app/config is available first)*

### Lab 12 — Quick Edit
**Goal:** Make a fast inline edit without the full editor.
1. **Verify:** Quick Edit is available (`tools/quick-edit`, or in `da.live/apps`).
2. Launch Quick Edit on a page; change a line of text; save.
3. Confirm the change in Preview.
**Expected:** Lightweight edit round-trip.
**Ref:** `/demo-docs/usecases/how-to-use-quick-edit`

### Lab 13 — Schedule Publish  ⚙️
**Goal:** Queue a page to go live at a future time.
1. **Verify:** Scheduler is available in DA for this org.
2. On a page, choose **Schedule** in the publish menu; set a date/time.
3. Confirm it appears in the schedule/queue.
**Expected:** A scheduled activation.
**Ref:** `/demo-docs/usecases/how-to-schedule-publish`

### Lab 14 — Request Publish  ⚙️
**Goal:** Route a publish through approval instead of publishing directly.
1. **Verify:** the Request-Publish workflow is enabled.
2. On a page, choose **Request Publish**; add a reviewer/note.
3. As approver, approve → page publishes.
**Expected:** Governed publish with an approval gate.
**Ref:** `/demo-docs/usecases/how-to-use-request-publish`

### Lab 15 — Media Library  ⚙️
**Goal:** Insert an image from the shared media library.
1. **Verify:** Media Library is available in the editor/apps.
2. In a page, insert an image → pick from the **Media Library**.
3. Publish; confirm the asset renders.
**Expected:** Centralized media reuse.
**Ref:** `/demo-docs/usecases/how-to-use-media-library`

### Lab 16 — Localize fragments
**Goal:** Serve a fragment in another language.
1. Open a fragment under `/fragments/`.
2. Create/locate its German counterpart under `/de/…`.
3. Confirm the German page renders the localized fragment.
**Expected:** Locale-aware fragment delivery (`/de/` is already live).
**Ref:** `/demo-docs/usecases/how-to-localize-fragments`

### Lab 17 — Translations & rollouts  ⚙️
**Goal:** Push English source content into a locale.
1. **Verify:** translation config exists (Config sheets) and `/de/` is set as a locale.
2. Start a translation job for a page into **de**; review the draft.
3. Publish the localized page; confirm on `…aem.live/de/…`.
**Expected:** Source → localized copy with a review gate.
**Ref:** `/demo-docs/usecases/how-to-manage-translations-and-rollouts`

### Lab 18 — Multi-Site Management (MSM)  ⚙️
**Goal:** Roll a blueprint change out to live copies.
1. **Verify:** MSM/live-copy config exists for wknd-advanced.
2. Change a blueprint element (e.g., nav); roll out to a live copy.
3. Confirm the copy updated while local overrides were preserved.
**Expected:** Governed structural propagation.
**Ref:** `/demo-docs/usecases/how-to-use-msm`

### Lab 19 — Clone the site (CloneIT)
**Goal:** Spin up a fresh copy of the site for a new demo.
1. **Verify:** CloneIT is available (`tools/cloneit` + `cloneit_token` worker are present).
2. Launch CloneIT; target a new org/repo; run the clone.
3. Open the cloned site and confirm content/config carried over.
**Expected:** A working duplicate site.
**Ref:** `/demo-docs/usecases/how-to-clone-demo-site`

### Lab 20 — Add new users  ⚙️
**Goal:** Grant a teammate access to the site.
1. **Verify:** you have admin rights on the org.
2. Add a user/group with read or write in the Permissions/access flow.
3. Have them confirm access.
**Expected:** A new collaborator onboarded.
**Ref:** `/demo-docs/usecases/how-to-add-new-users`

---

## Deferred to a later lab (need external connections)
These require services connected to the site before they'll run; not in this book:
Personalization (Adobe Target) · Experimentation · AEM Assets · Dynamic Media · Content Fragment overlay · html2json / json2html (no workers present yet).
