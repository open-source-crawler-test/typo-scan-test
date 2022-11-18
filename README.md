# RepoTypoScan Reusable Action [![CI](https://github.com/open-source-crawler-test/typo-scan-test/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/open-source-crawler-test/typo-scan-test/actions/workflows/ci.yml)


## Basic Usage

Create a `typo.yml` workflow file, and execute the typo scan on the current repository.

```yml
# .github/workflows/typo.yml

name: Typo Scan
on: 
 push:

jobs:
  test-action:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: ✅ Run action.yml to verify all steps pass
        uses: open-source-crawler-test/typo-scan-test@main
        with:
          repository: ${{ github.repository }}
          scan-exclude-match: '[''typos/**'', ''public/**'']'
          report-folder-name: typos-scan-output-artifact
```



## Scan External Repository

Alternatively, easily run this scan on an external repository

```yml
# .github/workflows/typo.yml

name: External Scan
on: 
 push:

jobs:
  test-action:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: ✅ Run action.yml to verify all steps pass
        uses: open-source-crawler-test/typo-scan-test@main
        with:
          repository: npm/registry
          scan-exclude-match: '[''typos/**'', ''public/**'']'
          report-folder-name: custom-folder-name
```