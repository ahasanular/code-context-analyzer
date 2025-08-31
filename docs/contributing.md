# Contributing Guide

Thank you for your interest in contributing to **Code Context Analyzer**!

This guide will help you get started with local development, testing, and submitting changes.

---

## 🧰 Prerequisites

- Python 3.10+
- `pip` or `poetry`
- Git

---

## 📦 Setting Up Locally

```bash
git clone https://github.com/ahasanular/code-context-analyzer.git
cd code-context-analyzer
pip install -r requirements.txt
```

> You can also use `poetry install` if you're using Poetry.

---

## 🧪 Running Tests

This project uses **pytest**.

```bash
pytest
```

To run tests with coverage:

```bash
pytest --cov=parsers
```

---

## 🧼 Code Style

- Follow **PEP8** for formatting
- Use **type hints** wherever possible
- Run `flake8` & `isort` before submitting

Format your import:
```bash
isort 
```


Check for linting errors:

```bash
flake8
```

---

## 📝 Submitting a Pull Request

1. Fork the repository
2. Create a new branch (`git checkout -b feature/my-new-feature`)
3. Make your changes
4. Write tests if applicable
5. Run tests and linters
6. Commit and push (`git commit -m "Add: my new feature"`)
7. Open a Pull Request against `master`

---

## 🔌 Adding a New Language Parser

1. Create a new file in `analyzer/parsers/` (e.g. `go_parser.py`)
2. Implement the `ParserProtocol`
3. Register it in the CLI (`parsers/__init__.py`)
4. Add tests for the parser

---

## 📚 Documentation

Documentation is powered by **MkDocs** and lives in the `docs/` folder.

To preview locally:

```bash
mkdocs serve
```
Or you can see them via
```bash
https://ahasanular.github.io/code-context-analyzer/
```

---

## 🌍 Code of Conduct

Please be respectful and inclusive in all interactions.
We follow the [Contributor Covenant](https://www.contributor-covenant.org/).

---

Thanks again for contributing! 💙
See [License](license.md).