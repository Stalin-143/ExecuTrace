<div align="center">

```
  ███████╗██╗  ██╗███████╗ ██████╗██╗   ██╗████████╗██████╗  █████╗  ██████╗███████╗
  ██╔════╝╚██╗██╔╝██╔════╝██╔════╝██║   ██║╚══██╔══╝██╔══██╗██╔══██╗██╔════╝██╔════╝
  █████╗   ╚███╔╝ █████╗  ██║     ██║   ██║   ██║   ██████╔╝███████║██║     █████╗  
  ██╔══╝   ██╔██╗ ██╔══╝  ██║     ██║   ██║   ██║   ██╔══██╗██╔══██║██║     ██╔══╝  
  ███████╗██╔╝ ██╗███████╗╚██████╗╚██████╔╝   ██║   ██║  ██║██║  ██║╚██████╗███████╗
  ╚══════╝╚═╝  ╚═╝╚══════╝ ╚═════╝ ╚═════╝    ╚═╝   ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚══════╝
```

# ExecuTrace

**Record, edit, and replay developer workflows**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/downloads/)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS-purple.svg)](#)

</div>

---

## About

ExecuTrace is a Python library and CLI tool that captures developer workflows and replays them reliably.

**What it does:**
- Records terminal commands from shell history
- Tracks file system changes (create, modify, delete)
- Saves workflows in JSON or XML format
- Replays workflows with multiple execution modes

**Why use it:**
- Automate repetitive development tasks
- Share procedures with team members
- Create reproducible environment setups
- Document complex workflows reliably
- Ensure consistent deployments

---

## Installation

### From PyPI (Global Library)
```bash
# Install globally from PyPI
pip install exectrace

# Verify installation
exectrace --help
```

### From Source (Development)
```bash
git clone https://github.com/Stalin-143/ExecuTrace.git
cd ExecuTrace
pip install -e .
```

---

## Publishing to PyPI

To publish ExecuTrace as a Python package to PyPI:

### Prerequisites
```bash
pip install build twine
```

### Build the Package
```bash
python -m build
```

This creates:
- `dist/exectrace-1.0.0.tar.gz` (source distribution)
- `dist/exectrace-1.0.0-py3-none-any.whl` (wheel)

### Upload to PyPI
```bash
# Upload to official PyPI (requires PyPI account)
twine upload dist/*

# Or test upload first
twine upload -r testpypi dist/*
```

### PyPI Account Setup
1. Create account at https://pypi.org/account/register/
2. Generate API token at https://pypi.org/manage/account/token/
3. Create `~/.pypirc`:
```
[distutils]
index-servers =
    pypi

[pypi]
repository = https://upload.pypi.org/legacy/
username = __token__
password = pypi_YOUR_TOKEN_HERE
```

---

## Quick Usage

```bash
# Record
exectrace record my-workflow
# ... run your commands ...
exectrace stop

# Replay
exectrace replay my-workflow --explain
```

---

## License

MIT License - See [LICENSE](LICENSE) for details.

