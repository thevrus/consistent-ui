# consistent-ui

A Claude Code skill that enforces UI consistency across an entire codebase — regardless of language, framework, or styling approach.

## What it does

Compares **every UI surface against every other UI surface** and against the project's design system, then surfaces drift in:

- **Spacing & layout** — off-scale paddings, inconsistent rhythm, mixed units
- **Typography** — heading drift, off-scale sizes, weight mixing
- **Color & theme** — hard-coded values, token bypass, dark-mode gaps
- **Components** — duplicate implementations, inline reimplementations, API drift
- **Iconography** — mixed libraries, size/stroke mismatch
- **Borders, radius, shadows / elevation** — inconsistent corners and depth
- **Interaction & motion** — hover/press/focus, durations, easing, focus rings
- **Forms** — input heights, label placement, error styling, required indicators
- **Page chrome** — headers, empty/loading/error states, toasts, navigation
- **Copy & microcopy** — capitalization, terminology, translation gaps (per locale)

Output is a **Consistency Health Score** (??/40), findings tagged **P0-P3** with file:line locations, systemic root-cause patterns, and a phased remediation plan.

## Stacks supported

Auto-detects and adapts patterns for:

- **Web — components**: React, Vue, Svelte, Angular, Solid, Astro, Qwik
- **Web — styling**: plain CSS/SCSS/Less, Tailwind / UnoCSS / Windi, styled-components, emotion, vanilla-extract, panda, stitches
- **Native iOS**: SwiftUI, UIKit
- **Native Android**: Jetpack Compose, View XML
- **Cross-platform mobile**: Flutter, React Native
- **Server-rendered templates**: Blade, ERB, Twig, Razor, JSP, Pug, Liquid, Handlebars, Phoenix HEEx, Django

Mixed-stack repos are scanned per profile and reported with combined plus per-stack scores.

## Install

### Via Claude Code (recommended)

In any Claude Code session:

```
/plugin marketplace add thevrus/consistent-ui
/plugin install consistent-ui@consistent-ui
```

That's it — the skill will be available globally.

### Manually (clone into your skills directory)

```bash
git clone https://github.com/thevrus/consistent-ui.git ~/.claude/skills/consistent-ui-source
ln -s ~/.claude/skills/consistent-ui-source/skills/consistent-ui ~/.claude/skills/consistent-ui
```

## Usage

```
/consistent-ui
/consistent-ui src/components/dashboard
/consistent-ui checkout-flow
```

Without an argument, scans the entire UI codebase. With an argument, restricts analysis to a path or feature.

## Output

1. **Detected stacks and locales** (confirmed before scanning)
2. **Discovered design system** (tokens, components, conventions)
3. **Consistency Health Score** with per-dimension breakdown
4. **Findings by severity** (P0 → P3) with locations and canonical alternatives
5. **Systemic patterns** — root-cause groupings
6. **Positive findings** — what's already consistent
7. **Remediation plan** in waves you can run independently

After the report, the skill asks whether to apply fixes immediately, run waves with confirmation, or stop at the report.

## When to use vs other skills

- Use **`consistent-ui`** for cross-surface drift across the whole codebase.
- Use **`/audit`** for technical quality (a11y, performance, anti-patterns) on a single surface.
- Use **`/polish`** for the final pre-ship micro-pass on one feature.

## Contributing

This is a **markdown-only skill** — no CLI binary, no companion executable, no runtime code. The behavior lives entirely in [`skills/consistent-ui/SKILL.md`](skills/consistent-ui/SKILL.md), which Claude Code loads directly. As a result:

- The [CLI hint protocol](https://code.claude.com/docs/en/cli-hint) (`<claude-code-hint />` markers on stderr) does **not** apply here. There is no CLI to emit one from.
- Improvements should be made by editing `SKILL.md` directly. New stack profiles, detection patterns, and dimension checks all live in that single file (see Appendix A for the per-stack pattern table).
- Bumps to `version` must be made in **both** `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` to keep the manifests in sync.

PRs welcome.

## License

MIT — see [LICENSE](LICENSE).
