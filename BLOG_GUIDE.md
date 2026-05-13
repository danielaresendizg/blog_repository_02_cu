# Blog Design & UX Guide
*Daniela Reséndiz — typingspace*

## Visual identity

- **Typography body:** Source Serif 4 (Google Fonts) — legible, editorial, serif for long-form reading
- **Typography titles:** Playfair Display — expressive, magazine-weight serif
- **Typography mono/kicker:** JetBrains Mono — for labels, tags, technical terms
- **Accent color:** `#c0392b` (Atlantic red) — links, kickers, blockquote borders
- **Interactive color:** `#0000ff` — hover states, glossary terms, SVG annotations
- **Background:** `#fff` white
- **Body text:** `#222`
- **Captions / meta:** `#999`, `font-family: system-ui`

---

## Layout

- **Wrap width:** 680px centered — optimal reading line length
- **Images full-bleed:** `margin: 2.5rem -48px` — breaks out of the wrap for visual impact
- **Image caption:** same offset as image, `font-size: .7rem`, system-ui
- **Drop cap:** first letter of first paragraph in Playfair Display

---

## Article structure

Every article should have:

1. **Topbar** — `← Blog` link back
2. **Hero** — kicker (JetBrains Mono, red) + H1 (Playfair) + byline
3. **Opening image** — full-bleed with caption and source credit
4. **Body** — paragraphs with inline citations linked to references
5. **Galleries** — grouped by historical moment with `gallery-year` label in mono red
6. **Video** — inline, `muted loop`, with caption
7. **Annotated maps** — SVG overlay with hover annotations (blue `#0000ff`)
8. **References** — `border-top: 2px solid #111`, system-ui, with DOI links

---

## Maps & spatial analysis

### Axial map (global integration)
- Source: DepthmapX analysis
- Color scale: cyan → blue → green → yellow → orange → red (low to high)
- Legend: always include gradient bar with "Low · segregated" / "High · integrated"
- Annotations: SVG overlay, `position: absolute`, `pointer-events: none` on SVG, `pointer-events: all` on groups
- Hover: `#0000ff` for label, line and dot — dot scales 50% larger

### Visibility / covisibility maps
- Source: Isovist analysis
- Caption must explain: what the measure means + what warm/cool tones indicate + which specific spaces stand out
- Always cite: Ortíz-Chao et al.

---

## Glossary tooltips

- Mark technical terms **only on first appearance** in the text
- Style: `color: #0000ff`, `border-bottom: 2px dotted #0000ff`
- On hover: **bold**, tooltip appears in **right margin** (not over text)
- Tooltip: `background: #0000ff`, white text, `position: fixed` positioned via JS
- Terms used so far:
  - *space syntax theory* — A theory of space and analytical tools for analysing the layout of space in buildings and cities.
  - *co-presence* — People who share and use a space without necessarily knowing each other — the raw material for community formation.

---

## Photo galleries

- Group by historical moment with a label: `font-family: JetBrains Mono`, `color: #c0392b`, uppercase
- Grid: 3 columns for 3 photos, 2 columns for 2 photos
- Images: `aspect-ratio: 4/3`, `object-fit: cover`, `filter: grayscale(20%)`
- Hover: color reveals, caption appears as overlay with `background: rgba(0,0,0,.78)`
- Caption should explain: social context + spatial dimension + how protest was detonated and amplified

---

## Citations & references

- In-text: link to `#ref-id` anchor in references section
- References section: `border-top: 2px solid #111`, alphabetical by author
- Always include DOI when available as `doi` link
- For open access: label as `open access` with direct URL
- Format: Author (Year) 'Title', *Journal*, vol(issue), pp. XX–XX. doi.

---

## UX patterns to explore for future entries

### Photo ↔ Map connection (to implement)

**Recommended: Guardian/D3 callout lines + StoryMap scroll pins**

- SVG hairlines connecting a zone in a historical photo to its location on a heat map
- On scroll: photo "cards" anchor themselves to GPS coordinates on the map
- At end of scroll sequence: all photos visible simultaneously across the campus — the spatial argument made visible
- Tech: Leaflet.js + Scrollama.js + static GeoJSON

**Other patterns researched:**
- Mapbox Storytelling (sticky split-screen scrollytelling) — NYT/WaPo style
- Leaflet + photo thumbnails with pulse markers and SVG leader lines
- Heat map click → drill down to photo clusters (The Pudding / CARTO)
- Scroll-triggered photo cards on map (Historypin / StoryMapJS)

---

## File structure per article

```
blog_repository_XX_[topic]/
├── index.html          # Article
├── images/
│   ├── cover.jpg       # Opening image
│   ├── [topic]_map.png # Spatial analysis maps
│   └── [event]_*.jpg   # Historical photos grouped by moment
└── [references].pdf    # Source PDFs for reference
```

---

## Sources & references for design inspiration

- The Atlantic — editorial typography, drop caps, red accent
- The Guardian — SVG annotation callouts
- The Pudding — scrollytelling, data-driven visual essays
- NYT / Mapbox Storytelling — sticky map + scroll narrative
- Historypin / StoryMapJS — photo cards pinned to map coordinates
- Ortíz-Chao, C.G. (2020) *Academia XXII*, 11(21) — space syntax CU
- Ortíz-Chao, C.G. et al. (2024) *Academia XXII*, 15(30) — visibility CU
