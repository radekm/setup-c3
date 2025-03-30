GitHub action which downloads C3 compiler and adds it to the PATH.

To use this action include the following step in your workflow:

```yaml
- uses: radekm/setup-c3@v2
  with:
    version: v0.7.0
```

Here's an example of a workflow:

```yaml
on: [push]

jobs:
  build:
    strategy:
      matrix:
        include:
          - os: macos-latest
            arch: arm64
          - os: ubuntu-latest
            arch: x64
          - os: windows-latest
            arch: x64
    runs-on: ${{ matrix.os }}
    name: Build
    steps:
      - uses: actions/checkout@v4
      - uses: radekm/setup-c3@v2
        with:
          version: v0.7.0
      - shell: bash
        run: c3c compile --lib somelib someprogram.c3
```
