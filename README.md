# GitHub Action: Run Sphinx Linkcheck and format the results
[![GitHub Action badge](https://github.com/manics/action-sphinx-linkcheck/workflows/test/badge.svg)](https://github.com/manics.action-sphinx-linkcheck/actions)

GitHub Action to run Sphinx Linkcheck and format the results into an easily readable format.

This action assumes the documentation was setup using
[`sphinx-quickstart`](https://www.sphinx-doc.org/en/master/usage/quickstart.html)
and must be run from the directory containing the Sphinx `conf.py` file.

## Optional input parameters
- `python-version`: Setup this version of Python, default empty (you must setup Python yourself)
- `requirements-file`: Install the requirements in this file, default empty (you must install requirements including Sphinx yourself)
- `sphinx-directory`: Directory containing Sphinx `conf.py`, default `.`
- `sphinx-options`: Value of `SPHINXOPTS`, default `-W --keep-going`

## Example

```yaml
name: Example workflow

on:
  pull_request:
  push:
  workflow_dispatch:

jobs:
  sphinx-docs:
    runs-on: ubuntu-22.04
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Run linkcheck and summarise results
        uses: manics/action-sphinx-linkcheck@main
        with:
          python-version: "3.11"
          requirements-file: docs/requirements.txt
          sphinx-directory: docs
```
