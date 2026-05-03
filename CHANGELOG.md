# Changelog

All notable changes to `consistent-ui` are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.2] — 2026-05-03

### Changed
- Removed non-spec `license` field from `SKILL.md` frontmatter (license is already declared in `plugin.json`, `marketplace.json`, and the `LICENSE` file).
- Added `$schema` to `plugin.json` for IDE autocomplete and validation against the official schemastore manifest.
- Removed invalid `$schema` URL from `marketplace.json` (no canonical schemastore entry exists for marketplace files yet).

### Fixed
- Spec compliance pass against official Claude Code plugin/skill documentation.

## [1.0.1] — 2026-05-03

### Added
- `.claude-plugin/marketplace.json` — makes the repo a self-installable single-plugin marketplace. Users can now install with:
  ```
  /plugin marketplace add thevrus/consistent-ui
  /plugin install consistent-ui@consistent-ui
  ```

## [1.0.0] — 2026-05-03

### Added
- Initial public release of the `consistent-ui` skill.
- Cross-codebase UI consistency auditing across web (React, Vue, Svelte, Angular, Solid, plain HTML/CSS, Tailwind, CSS-in-JS), native mobile (SwiftUI, UIKit, Jetpack Compose, Views, Flutter, React Native), and server-rendered templates (Blade, ERB, Twig, Razor, JSP, Pug, Liquid, Handlebars, Phoenix HEEx, Django).
- 10-dimension scan: spacing, typography, color, components, iconography, borders/radius/shadows, interaction & motion, forms, page chrome, copy & microcopy.
- Phase 0–4 workflow: stack detection → design system discovery → drift scan → P0–P3 report with health score → phased remediation plan with optional fix mode.
- MIT License.
