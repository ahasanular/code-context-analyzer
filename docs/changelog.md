# Changelog

All notable changes to this project will be documented in this file.

This project follows [Semantic Versioning](https://semver.org/).

---

## [0.1.0] - 2025-08-26

### Added
- Initial release of **Code Context Analyzer**
- CLI interface via `cca` command
- Support for analyzing:
  - Local directories
  - Remote GitHub repositories
- File discovery module with optional test skipping
- Parsers for:
  - Python (via `ast`)
  - JavaScript (via regex)
- Modular `Formatter` class to generate text summaries
- Clipboard copy support (`--no-copy`)
- CLI flags for `--depth`, `--lang`, `--max-files`, `--ignore-tests`
- Temporary directory context manager for safe GitHub repo cloning

---

## [0.2.2] - 2025-08-28

### Added
- File discovery module with ignore files from `.gitignore`, `custom_patterns` and `framework-specific`
- Modular `formatters/` full module with multiple formatter added.
- CLI flags removed `--depth`, `--lang`.
- CLI flags added `--ignore`.
- And some architectural change in codebase.

---

## [Unreleased]

### Planned
- Add support for TypeScript and Go parsing
- Interactive TUI or web viewer
- JSON and Markdown output formats
- Syntax highlighting in output
- VSCode extension

For detailed contribution guide, see [Contributing](contributing.md).