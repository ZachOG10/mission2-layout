# Timeline Pyramid: Design Specification

**Designer:** Zachariah Aondowase
**For:** Frontend Developer
**Reference build:** `index.html` (single file: HTML, CSS and JavaScript, no dependencies except the Inter web font)
**Live preview:** https://zachog10.github.io/mission2-layout/

## 1. Tool choice

The design was built directly as an interactive HTML/CSS/JS mockup. Reason: it shows the real click behaviour, layout and responsive behaviour, and the developer can reuse the code. A Figma style frame of 1440 x 1000 px was used as the desktop reference.

## 2. Structure

| Screen | What it shows |
| --- | --- |
| Pyramid view (home) | Title, subtitle, intro paragraph, five-layer pyramid with 19 clickable markers, two legends |
| Detail view | Opens when a marker is clicked: header, year, title, subfield, Event, Significance, "Also in this layer", previous/next |

Both views live on one page. The detail view replaces the pyramid view; there is no side panel.

## 3. Pyramid layers (base to apex)

| # | Layer | Colour | Markers |
| --- | --- | --- | --- |
| 1 | Foundations of AI | `#6366f1` | Before 1950, 1950, 1955, 1956 (Birth of AI) |
| 2 | Early AI & Symbolic Systems | `#8b5cf6` | 1956 Logic Theorist, 1966 ELIZA, 1966-1972 Shakey, 1970s First AI Winter, 1980s Expert Systems, 1986 Backpropagation |
| 3 | Machine Learning & Deep Learning | `#3b82f6` | 1997 Deep Blue, 2004-2007 DARPA, 2006-2009 Netflix Prize, 2009 ImageNet, 2012 AlexNet |
| 4 | Generative AI & LLMs | `#06b6d4` | 2014 GANs, 2017 Transformer, 2022 ChatGPT |
| 5 | Future of AI | `#2dd4bf` | Future (AGI) |

Reading order is bottom to top and, inside a layer, left to right then top to bottom, so the pyramid follows AI's historical progression. The First AI Winter (1970s) sits in layer 2 so it comes before the 1980s expert systems.

## 4. Subfield colour-coding (dot on each marker)

| Group | Dot colour | Markers |
| --- | --- | --- |
| Foundations & history | `#94a3b8` | Before 1950, Turing, 1955, 1956, First AI Winter |
| Symbolic AI & search | `#fbbf24` | Logic Theorist, Expert Systems, Deep Blue |
| Machine & deep learning | `#fb7185` | Backpropagation, Netflix Prize, ImageNet, AlexNet |
| Language & generative AI | `#e879f9` | ELIZA, GANs, Transformer, ChatGPT |
| Robotics & autonomy | `#4ade80` | Shakey, DARPA |
| Future: AGI | `#ffffff` | AGI |

Each marker is grouped by the first subfield listed in the research. The full subfield text appears on the detail page.

## 5. Colours (tokens)

| Token | Value | Use |
| --- | --- | --- |
| `--bg` | `#070d1c` | Page background (dark navy) |
| `--panel` | `#0b1426` | Cards |
| `--line` | `rgba(255,255,255,.09)` | Subtle borders |
| `--text` | `#ffffff` | Main text |
| `--muted` | `#a6b3cc` | Body copy |
| Subtitle | `#7dd3fc` | Subtitle line |

Layer colours are in section 3 (`--l1` to `--l5`). Layer shapes use the layer colour at 16% fill with an 80% outline.

## 6. Typography (Inter)

| Element | Size / weight |
| --- | --- |
| Page title | 34px / 800 (24px on mobile) |
| Subtitle | 16px / 500 |
| Intro | 14px / 400, line-height 1.6 |
| Layer label | 10px / 700, letter-spacing .08em, layer colour |
| Marker year | 10px / 700, layer colour |
| Marker title | 11px / 600 (12px on mobile) |
| Detail year | 64px / 800 (40px for long text, 44px mobile) |
| Detail title | 32px / 700 (24px mobile) |
| Detail body | 16px / 400, line-height 1.65 |

## 7. Pyramid geometry (desktop)

- Canvas: 860 x 620 px, centred in the page.
- Width at height y: `110 + 750 * y / 620` (flat top 110px wide, base 860px).
- Layer heights from apex: 100, 120, 150, 150, 100 px. Gap between layers: 4px.
- Marker: height 54px, radius 8px, gap 6px. Widths: layer 1 = 130px, layer 2 = 112px, layer 3 = 110px, layer 4 = 92px, layer 5 = 100px.
- Markers are aligned to the bottom of each layer; the layer label sits 9px from the top.
- Below 1440px wide the whole pyramid scales down to fit.

## 8. Interaction design

| State | Behaviour |
| --- | --- |
| Hover | Marker lifts 2px and fills with a tint of its layer colour |
| Focus (keyboard) | 2px white outline |
| Click | Opens the detail view and scrolls to the top |
| Selected | White marker with a layer-coloured glow (shown when returning to the pyramid) |
| Back | "Back to pyramid" button or the browser back button |
| Previous / Next | Steps through the 19 milestones in order, with "Milestone N of 19" |
| Also in this layer | Buttons to jump to other milestones in the same layer |

Each milestone has its own link (`#m0` to `#m18`) so it can be shared. All text in the detail view comes word for word from the research document.

## 9. Responsive behaviour

| Screen | Layout |
| --- | --- |
| Desktop (above 900px) | Wide pyramid with markers inside each layer (section 7) |
| Mobile and tablet (900px and below) | Pyramid becomes a centred stack of layer blocks that narrow toward the top (widths 100, 90, 80, 68, 56%); markers sit in a two-column grid with larger text. Legends wrap. Previous/next buttons stack full width |

## 10. Accessibility

- All markers are real buttons, reachable and usable by keyboard.
- The marker's subfield group is in its tooltip (title), and the detail page spells out the subfield in text, so colour is never the only signal.
- Focus moves to the milestone title when the detail view opens.
- Animations are turned off for users who prefer reduced motion.

## 11. Files to hand over

- `index.html`: working reference build (all styles and scripts inside).
- `design-spec.md`: this document.
- Research text: the milestone notes in the `M` array at the top of the script are the final content.
