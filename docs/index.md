# Code Context Analyzer

Welcome to the **Code Context Analyzer** documentation!

This tool provides a command-line interface (`cca`) to analyze the structural context of codebases — including functions, classes, constants, and file hierarchy. It supports Python and JavaScript and is designed to help developers, code reviewers, and documentation tools better understand code organization.

---

## 🚀 Quick Start

### 📦 Install via pip

```bash
pip install code-context-analyzer
```

## 📁 Analyze a local project
```bash
cca /path/to/project
```

## 🌐 Analyze a GitHub repository
```bash
cca https://github.com/pallets/flask --ignore/alembic/
```

## ⚙️ Features

- 📂 Recursive file discovery
  - Respects .gitignore
  - Skips hidden and test directories if specified
- 🧠 Parsers for Python and JavaScript
  - Extracts classes, functions, constants
- 🖥️ CLI interface using cca command
- 📋 Clipboard output support 
- 🔌 Modular architecture for future language extensions
- 🌐 Supports both local paths and GitHub URLs

## 🧩 Architecture Overview
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

## 📚 Documentation Sections
- [Usage](usage.md)
- [Architecture Overview](architecture.md)
- [Module Reference](modules.md)
- [Contributing](contributing.md)

## 📎 License
This project is licensed under the MIT License

For detailed usage guide, see [Usage](usage.md).