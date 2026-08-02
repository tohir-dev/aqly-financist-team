# Changelog

All notable changes to **Aqly Financist Team** are documented in this file.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- **Licence — added a free-use grant.** Personal use, internal business use, modification for your own
  use, and producing work product for yourself, your business, or your clients are now permitted at
  no charge. Redistribution, resale, sublicensing, repackaging, and building a competing product for
  distribution remain prohibited, and now apply to free users and purchasers alike. Work product you
  create with the skill is yours and is not restricted. The grant may be withdrawn for future
  versions but cannot be revoked for a version already obtained under it.
- **Install instructions** now point at the skill folder (`.../tree/main/financist-team`) rather than the
  repository root, which contains no `SKILL.md` and cannot be imported.

> These changes are live on `main`, so they already reach anyone importing from it, but they are not
> yet covered by a version tag.

## [1.0.0] — 2026-08-01

### Added

- Initial public release.
- 8 methodological lenses: theoretical, quant, empirical, risk, behavioral, macro-policy, execution, and corporate.
- Routing rules that pair assumptions with numerics on any pricing question and add the risk lens to any number the user will act on.
- Verification requirements: numerical results cross-checked against a second method, empirical claims requiring out-of-sample testing and a multiple-testing correction, and an as-of date or `UNVERIFIED` label on every actionable figure.
- An advisory guardrail that withholds market-timing calls and specific allocations on every question, without reducing analytical depth.

[Unreleased]: https://github.com/tohir-dev/aqly-financist-team/compare/v1.0.0...main
[1.0.0]: https://github.com/tohir-dev/aqly-financist-team/releases/tag/v1.0.0
