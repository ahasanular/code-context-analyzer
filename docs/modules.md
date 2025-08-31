# Module Reference

This page lists and describes the major modules and classes in **Code Context Analyzer**.

---

## 📂 `cli/`

### `__init__.py`

- **Function**: `app(argv=None)`
  - Entry point for the CLI interface.
  - Parses arguments, initializes analysis, and prints or copies results.
- Uses components from `analyzer/`, `parsers/`

---

## 📂 `analyzer/`

### `discovery.py`

- Recursively walks a directory and yields file paths and inferred languages based on extension.
- Skips directories in multiple step - .gitignore respected, then framework specific and lastly optionally test files.
---

### `clipboard.py`

- Uses `pyperclip` to copy output text to the system clipboard.
- Returns `True` on success, `False` on failure.

---
### `analyzer/parsers/`
- Responsible for parsing many kind of files found from the discovery.
- Have multiple parsers included - `PythonParser` `JsParser`.
---
## 📂 `repo_system`

- Handler for GitHub repository
- works with context manager session to automatically remove the repo after analysis.
---

## 📂 `formatters/`

- Responsible for formatting the parsed data into a hierarchical summary.
- Have multiple formatters included - `default` `html`, `json`, `yaml`.
---


## 📂 `utils/`

- Have temp directory manager
- and dto converter for report formatting

---

## 📂 `tests/` and `tests/test_parsers/`
- Use `pytest` to test:
  - File discovery logic
  - Parser outputs
  - Formatter correctness
  - CLI entry point behavior
---

## 📦 Summary

| Module                             | Role                            |
|------------------------------------|----------------------------------|
| `cli`                              | CLI entrypoint and orchestration |
| `discovery.py`                     | File collection                  |
| `clipboard.py`                     | Clipboard copy utility           |
| `repo_system`                      | GitHub/local repo resolution     |
| `formatters`                       | Summary formatting               |
| `python_parser.py`, `js_parser.py` | Language parsers              |
| `temp_dir.py`                      | Temporary directory context      |

For detailed system flow, see [Changelog](changelog.md).
