# Module Reference

This page lists and describes the major modules and classes in **Code Context Analyzer**.

---

## 📂 `cli/`

### `__init__.py`

- **Function**: `app(argv=None)`
  - Entry point for the CLI interface.
  - Parses arguments, initializes analysis, and prints or copies results.
- Uses components from `analyzer/`, `parsers/`, and `utils/`.

---

## 📂 `analyzer/`

### `discovery.py`

- **Function**: `discover_files(root, languages, max_files, ignore_tests)`
  - Recursively walks a directory.
  - Yields file paths and inferred languages based on extension.
  - Skips hidden directories, `__pycache__`, and optionally test files.

- **Constant**: `EXT_MAP`
  - Maps file extensions to language identifiers (e.g., `.py` → `python`).

---

### `formatter.py`

- **Class**: `Formatter`
  - Responsible for formatting the parsed data into a hierarchical summary.
  - Takes options like `depth`, `method_preview`, and truncation settings.

- **Key Methods**:
  - `format_project(parsed)`
  - `_compute_common_root(paths)`
  - `_build_header(...)`

---

### `clipboard.py`

- **Function**: `copy_to_clipboard(text)`
  - Uses `pyperclip` to copy output text to the system clipboard.
  - Returns `True` on success, `False` on failure.

---

### `repository_handler.py`

- **Class**: `RepositoryHandler`
  - Handles resolving a source location (local or GitHub).
  - Supports:
    - Cloning GitHub repos into temp directories
    - Copying local folders
    - Selecting a branch

- **Key Methods**:
  - `resolve_source(source, branch)`
  - `_clone_repo_to_temp(...)`

---

## 📂 `parsers/`

### `base.py`

- **Class**: `ParserProtocol` (Python Protocol)
  - Defines the interface for all language parsers.
  - Required method: `parse_file(self, path)`

---

### `python_parser.py`

- **Class**: `PythonParser`
  - Parses Python files using the `ast` module.
  - Extracts classes, function signatures, and constants.

- **Key Methods**:
  - `parse_file(path)`
  - `_sig_from_function(node)`

---

### `js_parser.py`

- **Class**: `JSParser`
  - Parses JavaScript source files using regular expressions.
  - Detects:
    - Class definitions
    - Function declarations
    - Exported functions

- **Constants**:
  - `RE_CLASS`, `RE_FN`, `RE_EXPORT_FN`

---

## 📂 `utils/`

### `temp_dir.py`

- **Function**: `temp_directory(suffix, prefix, dir, auto_cleanup)`
  - Context manager for creating and managing temporary directories.
  - Automatically removes directory after use if `auto_cleanup=True`.

---

## 📂 `tests/` and `tests/test_parsers/`

- Currently includes `__init__.py` placeholders.
- Use `pytest` to test:
  - File discovery logic
  - Parser outputs
  - Formatter correctness
  - CLI entry point behavior

---

## 📦 Summary

| Module                      | Role                            |
|-----------------------------|----------------------------------|
| `cli`                       | CLI entrypoint and orchestration |
| `discovery.py`              | File collection                  |
| `formatter.py`              | Summary formatting               |
| `clipboard.py`              | Clipboard copy utility           |
| `repository_handler.py`     | GitHub/local repo resolution     |
| `python_parser.py`, `js_parser.py` | Language parsers              |
| `temp_dir.py`               | Temporary directory context      |

For detailed system flow, see [Changelog](changelog.md).
