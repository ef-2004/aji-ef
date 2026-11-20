# Ellie Fivas — personal website

A single static page: `index.html` (all CSS inline, no build step). Keep it one page unless asked otherwise.

## Content rules

- Text Ellie supplies (About, clips) goes in **exactly as written** — do not copyedit. Flag possible typos in chat instead.
- Contact line must read: "Reach me at elliefivas@washsun.com or on Signal at @elliefivas.65."
- Clips go in `<ul class="clip-list">` as `<li>` items with `.outlet`, a headline `<a>`, and a `<time>`; remove the `.placeholder` paragraph once the first clip is added.
- To add a clip from a link, use the project skill `/add-clip <url>` (`.claude/skills/add-clip/SKILL.md`). Clips stay newest first, and headlines are copied exactly as published, never rewritten.

## Style guide

Keep all future changes consistent with this style. The palette is defined as CSS custom properties on `:root` in `index.html`; change colors there, not inline.

**References:** fonts inspired by ProPublica and The Atlantic; page organization from ProPublica; section-label style from The Washington Sun. **Colors: light blues, navy and browns only — no yellow** (Ellie's preference).

### Layout (ProPublica-style)
1. **Masthead:** a 6px navy bar at the top; the name huge, uppercase, left-aligned; the tagline (role + beat) in bold serif on the right, aligned to the bottom of the name.
2. **Nav bar** between two thin navy rules: a mono "REPORTING ON" kicker followed by beat links on the left; page links (About, Clips, Contact) on the right.
3. **Lead row:** About (wide column, first paragraph slightly larger) beside a Contact card (narrow column).
   - The headshot (`headshot.webp`, 168×168) sits to the left of the About text with a brown bottom border; on phones it stacks above the text at 140px. Don't display it larger than 168px — the file is low resolution.
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

### Color (light blues, navy, browns)
| Token | Light | Dark | Use |
|---|---|---|---|
| `--paper` | `#ffffff` | `#11161d` | background |
| `--ink` | `#141a22` | `#eef1f5` | text |
| `--rule` | `#1c2e4a` | `#c8d3e0` | thin rules |
| `--navy` | `#1c2e4a` | `#a9c8e6` | primary: top bar, section labels, primary button, links |
| `--sky` | `#a9c8e6` | `#3d5a7a` | light blue: tagline highlight, clip hover underline |
| `--sky-wash` | `#eaf2fa` | `#1a2533` | contact card background |
| `--brown` | `#7b4f2c` | `#d4a77c` | warm accent: contact card top border, clip outlet names, hovers |
| `--tan` | `#c7a17a` | `#9c7651` | link underlines in body copy |
| `--tan-wash` | `#f6efe7` | `#261f19` | placeholder/note backgrounds |

### Components
- **Section headings** use the Washington Sun label: an uppercase Inter word in a solid navy box sitting on a thin navy rule (`<h2 class="label"><span>…</span></h2>`). In dark mode the box turns light blue.
- **Buttons** are rounded pills: the primary one is navy and turns brown on hover; the secondary one has an outline.
- Links are navy with a tan underline in body copy.
- Keep it clean: white space, thin rules, no shadows, no gradients except the light-blue tagline highlight.
- Support dark mode via `prefers-color-scheme` for every new color.
