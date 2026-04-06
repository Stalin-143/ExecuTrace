# GitHub Packages Configuration Guide

## Publishing to GitHub Packages

This project is configured to automatically publish to GitHub Packages when a release is created.

### Automatic Publishing (GitHub Actions)

When you create a release on GitHub (using git tag), the workflow in `.github/workflows/publish-to-github-packages.yml` will:

1. Build the Python package
2. Publish to GitHub Packages Python registry
3. Make it available at: `https://github.com/Stalin-143/ExecuTrace/packages`

### Creating a Release

```bash
git tag -a v1.0.1 -m "Version 1.0.1"
git push origin v1.0.1
```

Or use GitHub's web interface to create a release from an existing tag.

### Manual Publishing to GitHub Packages

If you need to publish manually:

```bash
# Build the package
python -m build

# Install twine if not already installed
pip install twine

# Publish to GitHub Packages
python -m twine upload dist/* \
  --repository-url https://python.pkg.github.com/Stalin-143 \
  --username YOUR_GITHUB_USERNAME \
  --password YOUR_GITHUB_TOKEN
```

### GitHub Token

You'll need a GitHub Personal Access Token with `write:packages` scope:

1. Go to GitHub Settings → Developer settings → Personal access tokens
2. Generate new token with `write:packages` scope
3. Use token as password in twine commands

### Installing from GitHub Packages

Others can install your package from GitHub Packages:

```bash
# Create a .netrc file in your home directory
cat > ~/.netrc << EOF
machine python.pkg.github.com
login YOUR_USERNAME
password YOUR_TOKEN
EOF

# Then install
pip install --index-url https://python.pkg.github.com/Stalin-143 exectrace-workflow
```

### Workflow Details

The GitHub Actions workflow automatically:
- Runs on release creation
- Can be manually triggered via `workflow_dispatch`
- Uses `GITHUB_TOKEN` for authentication
- Requires no additional secrets setup

---

**Current Version:** 1.0.1  
**Repository:** https://github.com/Stalin-143/ExecuTrace  
**Packages:** https://github.com/Stalin-143/ExecuTrace/packages
