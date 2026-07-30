# WKND — DA Block Library (build guide)

Rebuilds the DA editor Library around **WKND's own blocks** with **travel** example content. Everything here is authored in **DA** (content, not code), under `blofft1/wknd-advanced/docs/library/`.

## How to apply
1. For each block below, create/edit the DA doc at the listed path and author the block table exactly as shown (block name in the top row, content underneath).
2. Update the **`docs/library/blocks`** sheet (`data` tab) to the curated list in the last section.
3. **Publish** `/docs/library/**`.
4. Reopen a page in the editor → the Library shows your WKND blocks.

*(Alternative: I can generate these as importable HTML and you pull them in via the DA Import app — say the word.)*

## Curated block set (16)
Hero · Cards · Columns · Teaser · Tabs · Table · Related Articles · Fragment · Embed · Modal · Search · Journey Map · FAQ · Product Grid · Quiz · Social Share
*(Dropped for the travel demo: the finance calculators, header/footer, n8n-form, dynamic.)*

---

## Reskin these (shared blocks — change content to travel)

### Hero — `/docs/library/blocks/hero`  · focal-point: **yes**
| Hero |
|---|
| *(image: mountain trail at sunrise)* |
| **The *Art* of the Perfect Getaway** |
| Explore · Wander · Belong |
| [Explore trips](/trips) |

### Cards — `/docs/library/blocks/cards`
| Cards |
|---|---|
| *(img: tent)* **Backcountry Camping** — Sleep under the stars on hand-picked routes. |
| *(img: mountain bike)* **Mountain Biking** — Trails for every level, guided or solo. |
| *(img: kayak)* **River Kayaking** — Paddle wild water with local guides. |

### Columns — `/docs/library/blocks/columns`
| Columns |
|---|---|
| **Why WKND** — We curate the stories, routes, and gear that turn *someday* into *this weekend*. | *(image: hikers on a ridge)* |

### Teaser — `/docs/library/blocks/teaser`
| Teaser |
|---|
| Dig into our library of trip guides and local tips to help you travel smarter. |
| [Explore our guides](/articles) |

### Tabs — `/docs/library/blocks/tabs`
| Tabs |
|---|
| **Summer** — Alpine treks, coastal towns, long light. |
| **Winter** — Snowshoe routes, cabins, aurora hunts. |
| **Shoulder season** — Fewer crowds, better prices. |

### Table — `/docs/library/blocks/table`
| Table |
|---|---|---|
| Destination | Region | Best season |
| Chamonix | Alps | Jul–Sep |
| Reykjavík | Iceland | Sep–Mar (aurora) |
| Banff | Canada | Jun–Sep |

### Related Articles — `/docs/library/blocks/related-articles`
| Related Articles (dynamic) |
|---|---|
| keywords | travel, trips, guides, destinations |
| excluded-keywords | noindex |

### Fragment — `/docs/library/blocks/fragment`
| Fragment |
|---|
| https://main--wknd-advanced--blofft1.aem.live/fragments/related-articles |

### Embed — `/docs/library/blocks/embed`
| Embed |
|---|
| https://www.youtube.com/watch?v=  *(a WKND trip film)* |

### Modal — `/docs/library/blocks/modal`
| Modal |
|---|
| **Before you book** — Trips require a deposit; free cancellation up to 14 days out. |
| [Close] |

### Search — `/docs/library/blocks/search`
| Search |
|---|
| *(no content — the block reads `/query-index.json`)* |

### Journey Map — `/docs/library/blocks/journey-map`
| Journey Map |
|---|
| **Inspire** — Browse destinations and trip films. |
| **Plan** — Compare seasons, gear, and guides. |
| **Book** — Reserve your spot and add-ons. |
| **Belong** — Join the WKND community and share your trip. |

---

## Create these (WKND-native blocks — new showcase docs)

### FAQ — `/docs/library/blocks/faq`
Each row is a question / answer pair.
| FAQ |
|---|---|
| How far ahead should I book? | Popular trips fill 2–3 months out; shoulder season is more flexible. |
| What's your cancellation policy? | Free cancellation up to 14 days before departure. |
| Is gear included? | Core gear is provided; a packing list is sent after booking. |

### Product Grid — `/docs/library/blocks/product-grid`
Points at a source that lists trips (auto-blocks the grid).
| Product Grid |
|---|
| https://main--wknd-advanced--blofft1.aem.live/trips/query-index.json |

### Quiz — `/docs/library/blocks/quiz`
| Quiz |
|---|---|---|---|
| Complete Message | You're a WKND traveler — here's your trip style. | | |
| Questions | Options | Correct | Snippet |
| What's your ideal pace? | Fast and packed | | You love variety. |
| | Slow and immersive | true | Depth over distance. |
| Mountains or coast? | Mountains | true | Peaks it is. |
| | Coast | | Salt air calls. |

### Social Share — `/docs/library/blocks/social-share`
| Social Share |
|---|
| *(no content — reads the page's canonical URL + title)* |

---

## Update the index — `docs/library/blocks` sheet (`data` tab)
Replace the rows with this curated set (all paths on **your** org):

| name | path | focal-point |
|---|---|---|
| Hero | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/hero | yes |
| Cards | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/cards | |
| Columns | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/columns | |
| Teaser | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/teaser | |
| Tabs | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/tabs | |
| Table | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/table | |
| Related Articles | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/related-articles | |
| Fragment | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/fragment | |
| Embed | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/embed | |
| Modal | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/modal | |
| Search | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/search | |
| Journey Map | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/journey-map | |
| FAQ | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/faq | |
| Product Grid | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/product-grid | |
| Quiz | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/quiz | |
| Social Share | https://content.da.live/blofft1/wknd-advanced/docs/library/blocks/social-share | |
