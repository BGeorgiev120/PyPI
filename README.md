# PyPI Publishing Tutorial

![DEV](https://img.shields.io/badge/Dev-Bojidar%20Georgiev%20-%20%2347b3ff)

A comprehensive guide to creating, structuring, and publishing Python packages to PyPI.

## Table of Contents

- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [License Setup](#license-setup)
- [Documentation](#documentation)
- [Building and Publishing](#building-and-publishing)
- [Updating Your Package](#updating-your-package)
- 

## Project Structure

Every PyPI module should follow this standardized directory structure:

```
project-root/
│
├── src/
│   └── your_module_name/
│       └── __init__.py
│
├── LICENSE
├── README.md
└── pyproject.toml
```

> **Note**: The folder name under `src/` must match your package name exactly.

## Configuration

### pyproject.toml Setup

The `pyproject.toml` file is the modern standard for Python package configuration. Here's a complete template:

```toml
[project]
name = "projectname"
version = "0.1.0"
description = "A short description of your module"
authors = [
    { name="Your Name", email="your.email@example.com" }
]
readme = "README.md"
license = { file="LICENSE" }
requires-python = ">=3.7"
dependencies = []

[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"

[tool.setuptools]
package-dir = {"" = "src"}

[tool.setuptools.packages.find]
where = ["src"]

```

### Version Numbering (Semantic Versioning)

Follow semantic versioning principles:

```
MAJOR.MINOR.PATCH (e.g., 1.2.3)
```

- **PATCH** (0.0.1): Bug fixes and patches
- **MINOR** (0.1.0): New features (backward compatible)
- **MAJOR** (1.0.0): Breaking changes (not backward compatible)

## License Setup

[Licence](https://www.gnu.org/licenses/gpl-3.0.html)

Copy the text starting from "GNU GENERAL PUBLIC LICENSE" so you can have valid licence

## Documentation

### README.md Best Practices

Your README.md should include:

- **Project title and description**
- **Installation instructions**
- **Usage examples**
- **API documentation or links**
- **Contributing guidelines**
- **License information**

This file will be displayed on your PyPI project page, so make it informative and well-formatted.

## Building and Publishing

### Prerequisites

Install the required build tools:

```bash
pip install build twine
```

### Local Testing

1. **Build your package locally:**
   ```bash
   python -m build
   ```
   This creates a `dist/` folder containing `.whl` and `.tar.gz` files.

### Publishing to PyPI

#### Step 1: Test on TestPyPI (Recommended)

First, test your package on TestPyPI:

```bash
twine upload --repository testpypi dist/*
```

You'll need to create an account at [test.pypi.org](https://test.pypi.org/) and generate an API token.

#### Step 2: Publish to PyPI

Once tested, upload to the main PyPI:

```bash
twine upload dist/*
```

Create an account at [pypi.org](https://pypi.org/) and generate an API token from your [account settings](https://pypi.org/manage/account/).

### API Token Setup

1. Go to your PyPI account settings
2. Generate a new API token
3. Use `__token__` as the username
4. Use your token (including the `pypi-` prefix) as the password

## Updating Your Package

### Release Process

1. **Update version number** in `pyproject.toml`
2. **Clean previous builds:**
   ```bash
   rm -rf dist/ build/ *.egg-info/
   ```
3. **Build new version:**
   ```bash
   python -m build
   ```
4. **Upload to PyPI:**
   ```bash
   twine upload dist/*
   ```

### For End Users

Users can upgrade to the latest version with:

```bash
pip install your-package-name --upgrade
```

## Best Practices

- **Use virtual environments** for development
- **Write comprehensive tests** before publishing
- **Follow PEP 8** style guidelines
- **Include type hints** for better code documentation
- **Use continuous integration** for automated testing
- **Tag releases** in your version control system
- **Keep a changelog** to document version changes

## Troubleshooting

### Common Issues

- **Import errors**: Ensure your package structure matches the `pyproject.toml` configuration
- **Version conflicts**: Check that your version number hasn't been used before
- **Authentication errors**: Verify your API token is correctly configured
- **Build failures**: Check that all dependencies are properly specified

## Resources

- [Python Packaging User Guide](https://packaging.python.org/)
- [PyPI Documentation](https://pypi.org/help/)
- [Semantic Versioning](https://semver.org/)
- [Choose a License](https://choosealicense.com/)

---

**Happy packaging!** 🐍📦 If you have some problems you can watch this tutorial:

<div align="center">

[![YOTUBETUTORIAL](https://img.youtube.com/vi/9Ii34WheBOA/0.jpg)](https://www.youtube.com/watch?v=9Ii34WheBOA)

</div>
