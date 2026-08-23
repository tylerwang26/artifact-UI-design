# artifact-ui-design

> An AI design skill that refuses to look like a template.

A design skill for **Claude Artifacts**, **Cursor**, and similar AI coding tools — built around the principle that every design decision should be *chosen*, not defaulted into.

Inspired by the aesthetic sensibility of [Awwwards](https://www.awwwards.com/), [Webby](https://www.webbyawards.com/), and [FWA](https://thefwa.com/) award-winners, and grounded in Scandinavian minimalism.

---

## The Problem

Every LLM defaults to the same three visual patterns regardless of the brief:

1. **Warm beige + high-contrast serif + terracotta orange** — Claude's own UI palette. Appearing in user work means the AI's fingerprint is showing.
2. **Near-black background + single neon accent** — Dark mode with fluorescent green or vermillion.
3. **Newspaper layout** — Hairline rules, zero border-radius, dense multi-column grids.

These aren't *bad* designs. The problem is they appear **regardless of the subject matter**. This skill breaks that reflex.

---

## How It Works

### Two-phase flow (non-skippable)

**Phase 1 — Token Plan**

Before writing any code, produce a four-line spec:

| Item | Requirement |
|---|---|
| **Color** | 4–6 named hex values with explicit roles: Base / Surface / Accent / Muted / Ink |
| **Type** | ≥2 roles: restrained display face + complementary body face. Defined scale + weight + tracking |
| **Layout** | One sentence describing the structural concept + ASCII wireframe of 2–3 alternatives |
| **Signature** | The single element the whole page will be remembered by — must carry the subject's own meaning |

**Phase 2 — Self-critique before code**

Run the plan against the brief. If swapping in a similar brief would produce the same answer, that item is a default — not a choice. Fix it, explain the change, then write the code. Every color and type scale must trace back to the plan.

---

## Design Rules

### Anti-patterns to avoid

Beyond the three main defaults, also avoid:

- `01 / 02 / 03` numbering as decoration (use only for actual sequences)
- Hero with "big number + small label + gradient accent" (template answer — unless it's a data dashboard)
- Scattered micro-animations (one choreographed moment beats ten scattered effects)

### Color system

Always define five roles: **Base, Surface, Accent, Muted, Ink**

⚠️ **WCAG contrast critical**: Low-contrast colors (e.g. mustard yellow, peach) must never be used on small text or icons. Use them only as large-area backgrounds with dark Ink text on top.

### Typography

- **9-scale hierarchy** mapped to Tailwind built-in classes (`text-xs` → `text-9xl`)
- **No arbitrary values** (`text-[42px]` won't work without a compiler)
- **CJK layout rules:**
  - Use `leading-relaxed` or `leading-loose` for Chinese (denser glyphs need more breathing room)
  - Never use `tracking-tighter` or `tracking-tight` on Chinese text
  - No `font-light` on small Chinese text (complex strokes need weight)
  - Manually break long Chinese headlines with `<br />` to preserve semantic phrasing

### Motion

Animation serves the subject. One well-timed reveal beats ten scatter effects. Always respect `prefers-reduced-motion`.

### Copy

- Write from the user's side, not the system's: "Notifications", not "Webhook Settings"
- Active voice: "Save changes", not "Submit"
- Errors guide, they don't apologize

---

## Chapter 9: Top-tier Digital Aesthetics (Awwwards / Webby / FWA)

When the brief calls for it, bring in these advanced techniques:

- **Negative space & borderless design** — No grey lines or shadows. Let precise padding/margin and subtle background tone shifts (`#FFFFFF` vs `#F7F5F2`) do the structural work.
- **Restrained controls** — UI elements appear only when needed, or are designed so flat and quiet that content (3D, large imagery, core argument) takes full visual priority.
- **Muted tones + high-contrast typography** — Morandi palette, grey-green, earth tones as ambient base. Extreme typographic tension (very large headings + modular grid) carries the structural weight.
- **Data as narrative** — If handling large datasets, transform them into visually charged cards (Spotify Wrapped–style). Kill cognitive load, don't build Excel.

---

## Technical Constraints (Claude Artifacts)

| Rule | Detail |
|---|---|
| **CSS** | Tailwind built-in utility classes only. No compiler → no arbitrary values |
| **Storage** | No `localStorage` / `sessionStorage`. State via `useState` / `useReducer` |
| **Output** | Single-file, inline CSS + JS |
| **Components** | No required props (or provide defaults). Default export required |
| **Forms** | No `<form>` tags. Use `onClick` / `onChange` |
| **Available packages** | `recharts`, `lucide-react`, `d3`, `lodash`, `mathjs`, `papaparse`, `xlsx`, `chart.js`, `tone`, `three` (r128, no `OrbitControls`, no `CapsuleGeometry`) |
| **External scripts** | Import from `https://cdnjs.cloudflare.com` only |

---

## Reference Images

| File | Content |
|---|---|
| `artifact-ui-01.png` | Token system structure + three real examples |
| `artifact-ui-02.png` | Same ruleset → three completely different visual outputs |
| `artifact-ui-03.png` | Three AI default looks to avoid + copywriting rewrites |
| `artifact-ui-04.png` | 8-role color system (Base/Surface/Accent/Muted/Ink) with low-contrast usage rules |
| `artifact-ui-05.png` | 9-level type scale (Tailwind classes) + four CJK golden rules |

Paste images directly into the prompt — more effective than text descriptions.

---

## Installation

**Claude Code:**
```bash
cp -r . ~/.claude/skills/artifact-ui-design/
```

**Cursor:**
Copy the body of `SKILL.md` into `.cursor/rules/artifact-ui-design.mdc` (no frontmatter).

**OpenClaw / Codex:**
```bash
cp -r . ~/.openclaw/workspace/skills/artifact-ui-design/
# or for project-scoped:
cp -r . .codex/skills/artifact-ui-design/
```

---

## License

MIT — use it, fork it, ship it.
