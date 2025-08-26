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
cca ./my_project --lang python --depth 2
```

## 🌐 Analyze a GitHub repository
```bash
cca https://github.com/pallets/flask --lang python --depth 2
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

## 📁 Project Structure
```bash
code_context_analyzer/
├── cli/
│   ├── __init__.py            # CLI app codes
├── analyzer/
│   ├── discovery.py          # File discovery logic
│   ├── formatter.py          # Output formatter
│   ├── repository_handler.py # GitHub/local repo handling
│   ├── clipboard.py          # Clipboard support
│   ├── parsers/              # Code parsers (Python, JS)
│   └── utils/                # Temporary directory helpers
└── tests/                    # Test suite
└── main.py                   # Entrypoint
```

## 📚 Documentation Sections
- [Usage](usage.md)
- [Architecture Overview](architecture.md)
- [Module Reference](modules.md)
- [Contributing](contributing.md)

## 📎 License
This project is licensed under the MIT License

For detailed usage guide, see [Usage](usage.md).