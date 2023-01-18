# Sphinx project with Markdown and Confluence support

A mostly empty Sphinx documentation project configured with support for content authored in Markdown and that can send its build output to an Atlassian Confluence Cloud space.

## Prerequisites

- Python 3.7+

## Components used

This is a lightly scaffolded Sphinx project that uses the following:

- [Sphinx](https://github.com/sphinx-doc/sphinx) for static documentation site generation.
- [Atlassian Confluence Builder](https://github.com/sphinx-contrib/confluencebuilder) for Confluence-compatible output and direct-to-Confluence publishing.
- [MyST Parser](https://github.com/executablebooks/MyST-Parser) to support Markdown source content.

## How it was built

You can init a Sphinx project that gets close to this one by running this `sphinx-quickstart` command:

```bash
# Prerequisites: Sphinx and the --extensions listed.
sphinx-quickstart \
  --project "PLACEHOLDER_PROJECT_NAME" \
  --author "PLACEHOLDER_AUTHOR" \
  -v "1.0" \
  --language "en" \
  --ext-autodoc \
  --ext-intersphinx \
  --extensions "sphinx_rtd_theme,sphinxcontrib.confluencebuilder,myst_parser" \
  --sep \
  docs
  ```
