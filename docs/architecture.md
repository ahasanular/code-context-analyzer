# Architecture Overview

This document provides an overview of the internal architecture of **Code Context Analyzer**.

---

## 🧱 High-Level Components

The project is composed of several modular layers:

```plaintext
User CLI (cca)
   ↓
Source Resolver (local path or GitHub URL)
   ↓
File Discovery (discover_files)
   ↓
Language Parsers (Python, JS)
   ↓
Formatter (structured summary)
   ↓
CLI Output (terminal or clipboard)
```

---

## 📁 Directory Structure

```plaintext
code_context_analyzer/
├── cli/
│   └── __init__.py        # CLI logic, defines `app()`
├── main.py                # Optional entry point script
├── analyzer/
│   ├── discovery.py       # File discovery logic
│   ├── formatter.py       # Formats parsed output
│   ├── repository_handler.py # Handles GitHub/local resolution
│   ├── clipboard.py       # Cross-platform clipboard copying
├── parsers/
│   ├── base.py            # ParserProtocol definition
│   ├── python_parser.py   # Python code parser using `ast`
│   ├── js_parser.py       # JavaScript parser using regex
├── utils/
│   └── temp_dir.py        # Temp directory context manager
```

---

## 🔄 Process Flow

1. **User invokes CLI**

   The user runs:

   ```bash
   cca <source> --lang python --depth 2
   ```

2. **RepositoryHandler resolves the source**

   - If local path: it validates the directory
   - If GitHub URL: it clones the repo to a temp dir

3. **`discover_files()` walks the directory**

   - Yields paths and their inferred language
   - Filters based on extension, test files, max files

4. **Parsers process each file**

   - Python parser uses `ast` to find classes, functions, constants
   - JS parser uses regex to extract functions/classes

5. **Formatter builds structured output**

   - Outputs hierarchy based on folder/module structure
   - Optional truncation or flattening via `depth`

6. **Output sent to terminal or clipboard**

   - If `--copy` is passed, summary is copied using `pyperclip`

---

## 🔌 Extensibility

To add support for a new language:

1. Create a new parser in `parsers/` (e.g. `go_parser.py`)
2. Implement the `ParserProtocol`
3. Register the parser in the CLI entrypoint

Example:

```python
from .go_parser import GoParser

PARSERS = {
    "python": PythonParser(),
    "js": JSParser(),
    "go": GoParser(),  # new
}
```

---

## 🧪 Testing and Maintenance

- All modules are designed to be testable independently
- Temp directories are safely handled via context manager
- CLI arguments can be tested via unit or integration tests

For detailed module documentation, see [Module Reference](modules.md).
