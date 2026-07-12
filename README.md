# ultra-css-template

[日本語版はこちら](README.ja.md)

A showcase and template of logic built entirely with cutting-edge CSS. The only JavaScript is a one-line `onload` in index.html (a loader that fetches and duplicates components) — all component logic, including state management, data fetching, and rendering, is done in CSS.

**Demo:** https://ultra-css-template.surahotoke.workers.dev/

## Requirements
Latest desktop Chrome (Chrome 150+ recommended). Chrome on iPhone is not supported, as it is WebKit-based. This project makes heavy use of freshly shipped features such as `@function` / `if()` / `::column::scroll-marker` / Anchor Positioning / `text-fit`, and scroll-triggered animations (`timeline-trigger` / `animation-trigger`).

## Components (components/)

| Component | Description |
| --- | --- |
| api-source | Receiver that turns css-api's SVG responses into scroll timelines |
| column-generator-demo | Customization example of the column-generator mechanism |
| dice-cube | A 3D dice that rotates as you scroll |
| digital-clock | A digital clock that receives the time from css-api and keeps ticking |
| duplicator-slot | An input slot whose elements can be duplicated with the enter key |
| function-render | Graph rendering of a formula defined with `@function` |
| macbook-keyboard | A MacBook keyboard built with nothing but counter-style |
| offset-colorful-css | A logo effect where particles on an offset-path trace the letters "CSS" (fires when scrolled into view) |
| todo-item / todo-list | A TODO list with filters |
| weather-display | Receives and displays weather data from css-api |

## Libraries (lib/)

- **api-getter** — Decodes the values that css-api encodes into SVG dimensions, using nothing but scroll timelines and animations. Also provides CSS functions for reading the HTTP status (`--api-status()`) and branching on success (`--api-ok()`)
- **column-generator** — Uses `columns` and `::column::scroll-marker` to generate a large number of drawable elements from a single element. Its mapping / self-mapping / navigate modes support assigning indexes, classes, and roles to elements, as well as 2D placement
- **duplicator-layout** — A layout mechanism that makes duplicator-slot work as a duplication origin inside a contenteditable area

## Embeds (embeds/)

- **comment** — A message-board UI backed by css-api: form POST, renaming (Popover + Anchor Positioning), and list display (SVG-as-img)

## Structure

```
components/  HTML loaded as Web Components (<style> + markup)
lib/         CSS mechanisms shared across components
property/    @property registrations (custom properties targeted by animations)
embeds/      Standalone pages for iframe embedding
utility.css  General-purpose CSS functions (--random, --get-bit, etc.)
```

## Related

- [css-api](https://github.com/surahotoke/css-api) — The data-supplying API this template uses

## License
MIT
