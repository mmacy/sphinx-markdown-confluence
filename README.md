# Sphinx project with Markdown and Confluence support

This lightly scaffolded Sphinx documentation project is configured with Markdown support and support for sending built documentation to an Atlassian Confluence Cloud space.

The goals of the this project are to make Sphinx-to-Confluence doc publishing easier for project maintainers and docs contributors:

:heavy_check_mark: Keep all the docs-related stuff, including the Sphinx config and output, in a single _docs/_ directory.

:heavy_check_mark: Hide all the Sphinx-related stuff from casual docs contributors so they see only their _*.md_ files (and TOCs) in the _docs/_ directory.

:heavy_check_mark: Preconfigure Sphinx to support Markdown instead of RST and to support publishing to a Confluence space.

## Prerequisites

- Python 3.7+

## Installation

<!-- TODO: Put all this in a container and then
           mount the local FS /docs directory. Maybe? -->

To prepare the Sphinx project in this repo to document your Python (or other) software project, follow these steps.

> :information_source: **TIP:** __Before proceeding with these steps, create and enter a [Python virtual environment](https://docs.python.org/3/library/venv.html) for all your Sphinx-related activities._

1. Clone this repository to your build environment (local or remote).

    ```bash
    # Clone this repo into your local dev/build environment
    git clone $URI_OF_THIS_REPO $LOCAL_CLONE_DIR
    ```

1. Move or copy the  _docs_ directory to the root of your software project.

    ```bash
    cd $LOCAL_CLONE_DIR          # The directory where you cloned this repo
    mv ./docs $YOUR_PROJECT_ROOT # Move docs/ dir to root of your project
    cd $YOUR_PROJECT_ROOT        # Move into your project's root dir
    ```

1. Run `pip` to install the dependencies for Sphinx and its extensions.

    ```bash
    # Install dependencies for Sphinx and Sphinx extensions
    pip3 install -r ./docs/.sphinx-config/requirements.sphinx.txt
    ```


## Configuration

> TODO: Confluence config guidance goes here.

## Usage

Run `sphinx-build` to build the docs.

```bash
# 4. Use Sphinx to build docs for your project.
#    Modify path to the `docs` directory accordingly
sphinx-build \
-b confluence \             # Build type / output format
-c ./docs/.sphinx-config \  # Location of Sphinx config.py
./docs \                    # Location of doc assets (*.md)
./docs/.sphinx-output       # Build output destination
```

```bash
# Example Sphinx build command and output (truncated at <SNIP> for brevity)
(sphinx) user@host:~/repos/your-repo/your-project$ sphinx-build -b confluence -c ./docs/.sphinx-config ./docs ./docs/.sphinx-output
Running Sphinx v5.3.0
loading intersphinx inventory from https://docs.python.org/3/objects.inv...
myst v0.18.1: MdParserConfig(commonmark_only=False, gfm_only=False, enable_extensions=[], <SNIP>
building [mo]: targets for 0 po files that are out of date
building [confluence]: targets for 6 source files that are out of date
updating environment: [new config] 6 added, 0 changed, 0 removed
reading sources... [100%] subdir/page3
looking for now-outdated files... none found
pickling environment... done
checking consistency... done
preparing documents... done
writing output... [100%] subdir/page3
build succeeded.
```

## About the Sphinx project

This Sphinx project scaffolds a documentation project that uses the following:

- [Sphinx](https://github.com/sphinx-doc/sphinx) for static documentation site generation.
- [Atlassian Confluence Builder](https://github.com/sphinx-contrib/confluencebuilder) for Confluence-compatible output and direct-to-Confluence publishing.
- [MyST Parser](https://github.com/executablebooks/MyST-Parser) to support Markdown source content.

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
