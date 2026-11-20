# Ellie Fivas — personal website

A single static page: `index.html` (all CSS inline, no build step). Keep it one page unless asked otherwise.

## Content rules

- Text Ellie supplies (About, clips) goes in **exactly as written** — do not copyedit. Flag possible typos in chat instead.
- Contact line must read: "Reach me at elliefivas@washsun.com or on Signal at @elliefivas.65."
- Clips go in `<ul class="clip-list">` as `<li>` items with `.outlet`, a headline `<a>`, and a `<time>`; remove the `.placeholder` paragraph once the first clip is added.

## Style guide

Keep all future changes consistent with this style. The palette is defined as CSS custom properties on `:root` in `index.html`; change colors there, not inline.

**References:** fonts inspired by ProPublica and The Atlantic; color scheme from The Washington Sun; page organization from ProPublica.

### Layout (ProPublica-style)
1. **Masthead:** a 6px yellow bar at the top; the name huge, uppercase, left-aligned; the tagline (role + beat) in bold serif on the right, aligned to the bottom of the name.
2. **Nav bar** between two thin black rules: a mono "REPORTING ON" kicker followed by beat links on the left; page links (About, Clips, Contact) on the right.
3. **Lead row:** About (wide column, first paragraph slightly larger) beside a Contact card (narrow column).
4. **Clips:** a full-width grid of stories below.
5. **Footer:** a thin rule with small uppercase mono text.
- Max content width 72rem, 1rem side gutter. Under 760px everything stacks into one column.

### Typography (Google Fonts)
| Role | Font |
|---|---|
| Name/masthead | **Instrument Serif**, uppercase, very large (condensed, high-contrast, like ProPublica's wordmark) |
| Headlines, tagline, body | **Newsreader** (classic editorial serif, like The Atlantic) |
| Nav, section labels, buttons | **Inter**, weights 600–700 |
| Kickers, dates, outlet names, footer | **IBM Plex Mono**, uppercase, letter-spaced (like The Atlantic's bylines) |

### Color (Washington Sun base + complements)
| Token | Light | Dark | Use |
|---|---|---|---|
| `--paper` | `#ffffff` | `#121212` | background |
| `--ink` | `#111111` | `#f1efe9` | text, rules |
| `--sun` | `#f8c91c` | `#f8c91c` | signature yellow: top bar, primary pill button, tagline highlight |
| `--sun-wash` | `#fff6d6` | `#2a2410` | contact card background |
| `--navy` | `#1f3a8a` | `#9db4f5` | links and hover (yellow's complement) |
| `--sky` | `#e6ecfa` | `#1a2238` | placeholder/note backgrounds |
| `--brick` | `#c2410c` | `#f08a5d` | small accents only (clip outlet names) |

### Components
- **Section headings** use the Washington Sun label: an uppercase Inter word in a solid black box sitting on a thin black rule (`<h2 class="label"><span>…</span></h2>`). In dark mode the box turns yellow.
- **Buttons** are rounded pills: the primary one is yellow, the secondary one has a black outline.
- Links are navy with a yellow underline in body copy.
- Keep it clean: white space, thin rules, no shadows, no gradients except the yellow tagline highlight.
- Support dark mode via `prefers-color-scheme` for every new color.
