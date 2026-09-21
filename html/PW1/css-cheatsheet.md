# CSS Cheat Sheet — CV Stylesheet

One-line explanation for every property and selector type used in `cv.html`,
grouped by purpose. Use this to prep for explaining the code to your teacher.

## Font & typeface properties

| Property | What it does |
|---|---|
| `font-family` | Sets the typeface, trying each name in order until one is available (a "fallback stack"). |
| `font-size` | Sets the size of the text. |
| `font-weight` | Sets boldness (`bold`, `normal`, or a numeric value). |
| `font-style` | Sets `italic` vs `normal` slanting of the text. |
| `font-variant` | Shorthand that can switch letters to small capitals (`small-caps`). |
| `font-variant-caps` | Longhand version of the above — more specific control over capital-letter variants (here: `all-small-caps` turns *everything*, including what would be lowercase, into small caps). |
| `font-variant-numeric` | Controls how numerals are drawn — here, `lining-nums` keeps digits at a uniform height (like the digits on a calculator), used on dates so they line up neatly. |
| `font-variant-ligatures` | Turns on typographic ligatures — automatic joining of certain letter pairs (like "fi" merging into one glyph) if the font supports it. |
| `font-kerning` | Turns on kerning — the font's built-in adjustment of spacing between specific letter pairs (e.g. tightening "AV") for better visual balance. |
| `font-stretch` | Requests a condensed or expanded width variant of the font, if the font family provides one (`normal` = no stretch requested). |

## Color

| Property | What it does |
|---|---|
| `color` | Sets the text color. |
| `background-color` | Sets the fill color behind an element (used on table headers and the striped rows). |

Colors here mostly use `rgba(26, 62, 92, α)` — the same ink-blue RGB value
repeated everywhere, with only the fourth number (`α`, the opacity, 0–1)
changed. That's what makes the "muted" text tones read as *lighter versions
of the same color* instead of unrelated grays.

## Text decoration & emphasis

| Property | What it does |
|---|---|
| `text-decoration` | Shorthand to turn an underline/strikethrough on or off. |
| `text-decoration-line` | Longhand: which line to draw (`underline`, `line-through`, etc.). |
| `text-decoration-style` | How that line looks: `solid`, `dotted`, `double`, etc. |
| `text-decoration-color` | What color that line is drawn in. |
| `text-emphasis-style` | Draws small marks (dots, circles...) above/beside each character — like a highlighter built into the font rendering. Used on `<em>` as a pun ("emphasis" marks on the emphasis tag). |
| `text-emphasis-color` | Sets the color of those emphasis marks. |
| `text-shadow` | Draws a soft drop-shadow behind text (`x-offset y-offset blur color`). |
| `text-transform` | Forces text case: `uppercase`, `lowercase`, `capitalize`. |

## Spacing, indentation & alignment

| Property | What it does |
|---|---|
| `letter-spacing` | Extra space added between individual letters (tracking). |
| `word-spacing` | Extra space added between words. |
| `line-height` | Vertical space between lines of text within a paragraph. |
| `text-align` | Horizontal alignment of a text block (`left`, `center`, `justify`). |
| `text-align-last` | Alignment specifically of a paragraph's *last* line, which `text-align: justify` normally leaves alone. |
| `text-justify` | Refines *how* justified text is stretched to fill the line — `inter-word` adds the extra space between words rather than inside them. |
| `text-indent` | Indents just the first line of a block of text (classic print-style paragraph indent). |
| `hyphens` | Lets the browser automatically hyphenate long words at line breaks. |
| `white-space` | Controls whether text is allowed to wrap; `nowrap` (used on `<time>`) keeps a date from breaking across two lines. |
| `word-wrap` / `overflow-wrap` | Two names for the same feature: allows a very long unbroken word (like a long URL) to break instead of overflowing the page. `word-wrap` is the older name, kept for legacy support. |
| `word-break` | Similar idea but more aggressive — can break *anywhere*, even mid-word, used on the address block so long email addresses wrap. |
| `tab-size` | How many spaces wide a tab character renders as (mostly relevant to `<pre>`-like text; harmless here). |
| `vertical-align` | Aligns an inline element against the surrounding text — used to center the small ORCID icon on the text baseline. |

## Generated content & counters

| Property | What it does |
|---|---|
| `content` | Inserts extra text that isn't in the HTML at all — used twice: to print the auto-generated section number, and to add a small "↗" arrow after external links. |
| `counter-reset` | Creates a counter (named `section-counter`) and sets it to zero, declared once on `body`. |
| `counter-increment` | Adds 1 to that counter every time a `.section-title` (an `<h2>`) appears. |

Together these three give you automatic "1. About Me", "2. Work
Experience"... numbering without typing the numbers by hand — if you add or
reorder a section, the numbers update themselves.

## Lists & tables

| Property | What it does |
|---|---|
| `list-style-type` | Which bullet/marker a list uses (`circle` for `<ul>`, `decimal` for `<ol>`). |

## Selectors used (not properties, but worth being able to name)

| Selector type | Example in the file | What it matches |
|---|---|---|
| Type selector | `h2`, `p`, `a` | Every element of that tag name. |
| ID selector | `#cv-title` | The one element with `id="cv-title"` (the `<h1>`). |
| Class selector | `.section-title`, `.lead`, `.job-meta` | Every element carrying that `class="..."` attribute. |
| Descendant combinator (space) | `tbody tr` (implicit in some rules) | Any matching element *nested anywhere inside* another. |
| Child combinator `>` | `dl > dt` | Only a `dt` that is a *direct* child of `dl` (not nested deeper). |
| Adjacent sibling `+` | `h2 + p` | A `p` that comes *immediately* after an `h2`, same parent. |
| General sibling `~` | `h1 ~ address` | Any `address` that comes *anywhere after* `h1`, same parent (not necessarily immediately). |
| Attribute selector (presence) | `img[alt]` | An `img` that has an `alt` attribute at all, regardless of its value. |
| Attribute selector (starts-with) `^=` | `a[href^="mailto:"]` | An `a` whose `href` *starts with* `mailto:`. |
| Attribute selector (contains) `*=` | `a[href*="doi.org"]` | An `a` whose `href` contains `doi.org` *anywhere* in the string. |
| Pseudo-class (link states) | `a:link`, `a:visited`, `a:hover`, `a:focus`, `a:active` | The five different states a link can be in — unvisited, already clicked, mouse-over, keyboard-focused, currently being clicked. |
| Pseudo-class (structural) | `:first-of-type`, `:last-of-type` | The first / last sibling of a given tag among its siblings — used to highlight the most-recent and oldest entries in each list. |
| Pseudo-class (language) | `:lang(en)` | Elements within content marked as English (via the `lang="en"` on `<html>`). |
| Pseudo-element (generated text) | `::before`, `::after` | Injects generated `content` immediately before/after an element's real content. |
| Pseudo-element (partial text) | `::first-letter`, `::first-line` | Targets just the first letter, or just the first rendered line, of a block of text — used for the drop-cap-style first letter and small-caps first line of the intro paragraph. |

## Quick self-test

If you want to check you can explain the file, try answering these out loud:
1. Why does the section numbering ("1. About Me", "2. Work Experience"...)
   update itself instead of being typed by hand?
2. Why do all the "muted" grays in the file look related to each other
   instead of random?
3. What's the difference between `text-decoration-line` and
   `text-decoration-style`?
4. Why does `a[href*="doi.org"]` only affect some links and not others?
5. What would happen visually if you deleted `hyphens: auto;`?
