# jmychn.com

Personal site for Jimmy Chen — <https://jmychn.com/> (served by GitHub Pages, also at <https://jimmychen7.github.io/>).

Plain HTML and CSS. There is no build step: edit the files and push.

```
index.html      the page
404.html        not-found page (GitHub Pages serves it automatically)
css/style.css   all styles
fonts/          Inter, self-hosted (SIL Open Font License — see fonts/OFL.txt)
img/            favicon, touch icon and link-preview image
```

To preview locally, serve the folder from its root (paths are root-relative):

```bash
python3 -m http.server 8000
```

## Principles

- **Content first, enhancement second.** The name and links are in the HTML. The LinkedIn badge is loaded by a
  third-party script that content blockers often stop, so it is treated as an upgrade: when it renders it replaces the
  native fallback; when it can't, the page still says who it belongs to.
- **Respect the visitor's settings.** Dark by design, light when the system asks for it. Motion only runs when
  `prefers-reduced-motion` allows it. Reduced transparency, increased contrast, forced colours and print are handled.
- **Accessible by default.** One `<h1>`, landmark elements, visible keyboard focus, labelled new-tab links, 44px+ tap
  targets.
- **Fast and self-contained.** One stylesheet, one self-hosted variable font, inline SVG icons. The only third-party
  request is the LinkedIn badge.
- **Modern CSS, no tooling.** Cascade layers, nesting, design tokens with `light-dark()` and `oklch()`, logical
  properties, fluid sizing with `clamp()`. Everything used is Baseline Widely Available.

## Components

All in `css/style.css`, under `@layer components`:

| Class        | What it is                                                              |
| ------------ | ----------------------------------------------------------------------- |
| `.ambient`   | Drifting gradient background with film grain                            |
| `.card`      | The glass surface                                                       |
| `.identity`  | Monogram, name and profile link, with the LinkedIn badge as enhancement |
| `.avatar`    | Monogram disc                                                           |
| `.actions`   | Stack of full-width buttons                                             |
| `.button`    | Glass button; `.button--primary` is the filled variant                  |
| `.message`   | Heading and supporting line (404 page)                                  |

Colours, radii and spacing are custom properties in `@layer tokens` — change them there.
