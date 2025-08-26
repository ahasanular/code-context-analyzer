# Usage Guide

This guide explains how to use the `cca` command-line interface to analyze source code.

---

## 🔧 Basic Command

```bash
cca <source> [options]
```

### Examples

Analyze a local directory:

```bash
cca ./my_project --lang python --depth 2
```

Analyze a GitHub repository:

```bash
cca https://github.com/pallets/flask --lang python
```

---

## ⚙️ CLI Options

| Option            | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `<source>`        | Path to a local directory or a GitHub repo URL                             |
| `--lang`          | Comma-separated list of languages to analyze (e.g., `python,js`)           |
| `--depth`         | Hierarchy depth for formatted output                                        |
| `--max-files`     | Maximum number of files to process                                          |
| `--ignore-tests`  | Skip test files like `test_*.py` or `*.spec.js`                             |
| `--branch`        | Git branch to use (only applies when source is a GitHub repository)        |
| `--copy`          | Copy the formatted output to clipboard                                      |
| `--help`          | Show help message                                                           |

---

## 🧠 Language Support

Currently supported languages:

- Python (`.py`)
- JavaScript (`.js`)

---

## 🧪 Tips

- Use `--depth 1` to see a flat summary
- Combine `--ignore-tests` and `--max-files` for faster scans
- Use `--copy` to paste summaries into docs or PRs

---

## 📝 Output Example

```plaintext
project/
├── module_a/
│   ├── file1.py (2 classes, 3 functions)
│   └── file2.py (1 function)
└── module_b/
    └── file3.js (1 class, 2 exported functions)
```

---

For more details on internals, see [Architecture](architecture.md).
