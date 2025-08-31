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
├── /
│   ├── main.py
│   └── __init__.py
├── analyzer/
│   ├── clipboard.py
│   ├── discovery.py
│   └── __init__.py
├── analyzer\parsers/
│   ├── base.py
│   ├── js_parser.py
│   ├── python_parser.py
│   └── __init__.py
├── cli/
│   └── __init__.py
├── dto/
│   ├── models.py
│   └── __init__.py
├── formatters/
│   ├── base.py
│   ├── default.py
│   ├── factory.py
│   ├── html_formatter.py
│   ├── json_formatter.py
│   ├── yaml_formatter.py
│   └── __init__.py
├── repo_system/
│   ├── handler.py
│   ├── session.py
│   └── __init__.py
└── utils/
    ├── dto_converter.py
    ├── temp_dir.py
    └── __init__.py
```

---

## 🔄 Process Flow

1. **User invokes CLI**

   The user runs:

   ```bash
   cca <source> --ignore <some, ingore, patterns>
   ```

2. **RepositoryHandler resolves the source**

   - If local path: it validates the directory
   - If GitHub URL: it clones the repo to a temp dir

3. **walks through the directory**

   - Yields paths and their inferred language
   - Filters based on extension, test files, max files

4. **Parsers process each file**

   - Python parser uses `ast` to find classes, functions, constants
   - JS parser uses regex to extract functions/classes

5. **Formatter builds structured output**

   - Outputs hierarchy based on folder/module structure
   - Optional truncation

6. **Output sent to terminal or clipboard**

   - If `--no-clipboard` is passed, summary is copied automatically

---

## 🔌 Extensibility

To add support for a new language:

1. Create a new parser in `parsers/` (e.g. `go_parser.py`)
2. Implement the `ParserProtocol`
3. Register the parser in registry

Example:

```python
from .go_parser import GoParser

registry = {
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
