# fishfyi-embed

[![npm](https://img.shields.io/npm/v/fishfyi-embed)](https://www.npmjs.com/package/fishfyi-embed)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/fishfyi-embed)

Embed **FishFYI** widgets — fish, glossary terms, interactive tools, and inline elements — on any website. **10 widget types**, zero dependencies, Shadow DOM style isolation, 4 built-in themes (light, dark, sepia, auto), 2 styles (modern, organic), and live data from the [FishFYI](https://fishfyi.com) database.

Every widget includes a "Powered by FishFYI" backlink directing readers to the full reference.

> **Try the interactive widget builder at [widget.fishfyi.com](https://widget.fishfyi.com)**

## Quick Start

```html
<!-- Place widget div where you want it to appear -->
<div data-fishfyi="entity" data-slug="fish" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
```

That's it. The widget fetches data from the FishFYI API and renders with full style isolation.

## Widget Types

| Type | Usage | Description |
|------|-------|-------------|
| `entity` | `<div data-fishfyi="entity" data-slug="..."></div>` | Entity detail card — species, bird, fish, plant, or dinosaur |
| `glossary` | `<div data-fishfyi="glossary" data-slug="..."></div>` | Glossary term definition with cross-references |
| `guide` | `<div data-fishfyi="guide" data-slug="..."></div>` | Guide summary card with key takeaways |
| `compare` | `<div data-fishfyi="compare" data-slug="..."></div>` | Side-by-side entity comparison |
| `search` | `<div data-fishfyi="search" data-slug="..."></div>` | Search box linking to the full database |
| `iucn-badge` | `<div data-fishfyi="iucn-badge" data-slug="..."></div>` | IUCN conservation status badge with 9 status levels |
| `water-type` | `<div data-fishfyi="water-type" data-slug="..."></div>` | Freshwater/Saltwater/Brackish colored badge |
| `iucn-inline` | `<div data-fishfyi="iucn-inline" data-slug="..."></div>` | Inline IUCN status colored pill |
| `water-inline` | `<div data-fishfyi="water-inline" data-slug="..."></div>` | Inline water type colored pill |
| `taxonomy-inline` | `<div data-fishfyi="taxonomy-inline" data-slug="..."></div>` | Italic scientific binomial name |

## Widget Options

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-fishfyi` | entity, compare, glossary, guide, search, [tools] | required | Widget type |
| `data-slug` | e.g. "fish" | — | Entity slug from the FishFYI database |
| `data-theme` | light, dark, sepia, auto | light | Visual theme (`auto` follows OS preference) |
| `data-styleVariant` | modern, organic | modern | Widget design style |
| `data-size` | default, compact, large | default | Widget size |
| `data-placeholder` | any string | "Search Fish..." | Search box placeholder |

## Themes

```html
<!-- Light (default) -->
<div data-fishfyi="entity" data-slug="fish" data-theme="light"></div>

<!-- Dark -->
<div data-fishfyi="entity" data-slug="fish" data-theme="dark"></div>

<!-- Sepia -->
<div data-fishfyi="entity" data-slug="fish" data-theme="sepia"></div>

<!-- Auto — follows OS dark/light preference -->
<div data-fishfyi="entity" data-slug="fish" data-theme="auto"></div>
```

## Styles

```html
<!-- Modern (default) — clean lines, rounded corners, accent gradients -->
<div data-fishfyi="entity" data-slug="fish" data-styleVariant="modern"></div>

<!-- Organic — natural curves, earth-tone aesthetics, field-guide look -->
<div data-fishfyi="entity" data-slug="fish" data-styleVariant="organic"></div>
```

## Web Components (Custom Elements)

As an alternative to `data-*` attributes, you can use native HTML custom elements:

```html
<!-- Custom element form -->
<fishfyi-entity slug="fish" theme="light"></fishfyi-entity>
<fishfyi-compare slugs="fish,other-slug"></fishfyi-compare>
<fishfyi-search placeholder="Search Fish..."></fishfyi-search>

<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
```

Use `style-variant` (not `style`) to avoid conflicts with the HTML reserved `style` attribute.

## Examples

### Entity Card

```html
<div data-fishfyi="entity" data-slug="fish" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
```

### Side-by-Side Comparison

```html
<div data-fishfyi="compare" data-slugs="fish,other-slug"></div>
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
```

### Search Box

```html
<div data-fishfyi="search" data-placeholder="Search Fish..."></div>
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
```

### Glossary Term

```html
<div data-fishfyi="glossary" data-slug="example-term" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
```

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
```

### Specific version (production stability)

```html
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1.0.0/dist/embed.min.js"></script>
```

### npm (for bundlers)

```bash
npm install fishfyi-embed
```

```javascript
import 'fishfyi-embed';
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site
- **Zero dependencies**: No jQuery, React, or any external library
- **2 styles**: Modern (accent gradients) and Organic (natural curves, field-guide aesthetic)
- **4 themes**: Light, Dark, Sepia, Auto (OS preference detection)
- **CORS**: FishFYI API has CORS enabled for all origins
- **MutationObserver**: Works with dynamically added elements (SPAs)
- **IntersectionObserver**: Lazy loading — widgets only fetch when entering viewport (200px margin)
- **Rich Snippets**: DefinedTerm JSON-LD injected for glossary widgets
- **Bundle size**: Tree-shaken per site — only includes tools available on FishFYI

## Learn More About Fish

Visit [fishfyi.com](https://fishfyi.com) — FishFYI is a comprehensive fish reference with interactive tools, guides, and developer resources.

- **API docs**: [fishfyi.com/developers/](https://fishfyi.com/developers/)
- **Widget builder**: [widget.fishfyi.com](https://widget.fishfyi.com)
- **npm package**: [npmjs.com/package/fishfyi-embed](https://www.npmjs.com/package/fishfyi-embed)
- **GitHub**: [github.com/fyipedia/fishfyi-embed](https://github.com/fyipedia/fishfyi-embed)

## Nature FYI Family

Part of [FYIPedia](https://fyipedia.com) — open-source developer tools ecosystem. Nature FYI covers species taxonomy, ornithology, marine biology, botany, and paleontology. Hub: [naturefyi.com](https://naturefyi.com).

| Site | Domain | Focus | Package |
|------|--------|-------|---------|
| SpeciesFYI | [speciesfyi.com](https://speciesfyi.com) | Species taxonomy, biodiversity, IUCN conservation status | [npm](https://www.npmjs.com/package/speciesfyi-embed) |
| BirdFYI | [birdfyi.com](https://birdfyi.com) | 11,251 birds, biometrics, conservation, habitats | [npm](https://www.npmjs.com/package/birdfyi-embed) |
| **FishFYI** | [fishfyi.com](https://fishfyi.com) | 35,729 fish, game fishing, aquarium care, compatibility | **[npm](https://www.npmjs.com/package/fishfyi-embed)** |
| PlantFYI | [plantfyi.com](https://plantfyi.com) | 379,774 plants, hardiness zones, bloom seasons, gardening | [npm](https://www.npmjs.com/package/plantfyi-embed) |
| DinoFYI | [dinofyi.com](https://dinofyi.com) | 6,142 dinosaurs, geological periods, paleontology | [npm](https://www.npmjs.com/package/dinofyi-embed) |

## Embed Widget

Embed [FishFYI](https://fishfyi.com) widgets on any website with [fishfyi-embed](https://widget.fishfyi.com):

```html
<script src="https://cdn.jsdelivr.net/npm/fishfyi-embed@1/dist/embed.min.js"></script>
<div data-fishfyi="entity" data-slug="example"></div>
```

Zero dependencies · Shadow DOM · 4 themes (light/dark/sepia/auto) · [Widget docs](https://widget.fishfyi.com)

## License

MIT — see [LICENSE](./LICENSE).

Built with care by [FYIPedia](https://fyipedia.com).
