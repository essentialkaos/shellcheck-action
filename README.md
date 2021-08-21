<p align="center"><a href="#readme"><img src="https://gh.kaos.st/shellcheck-action.svg"/></a></p>

<br/>

Action for checking scripts with [Shellcheck](https://github.com/koalaman/shellcheck).

### Usage

Create file `.github/workflows/shellcheck.yml`.

Add next code to it:

```yml
name: CI

on:
  push:
    branches: [master, develop]
  pull_request:
    branches: [master]

jobs:
  Shellcheck:
    name: Shellcheck
    runs-on: ubuntu-latest

    steps:
      - name: Code checkout
        uses: actions/checkout@v2

      - name: Check scripts with Shellcheck
        uses: essentialkaos/shellcheck-action@v1
        with:
          severity: error
          format: gcc
          shell: dash
          files: src/script1.sh src/script2.sh

```

You can disable specific checks through environment variables:

```yml
      - name: Check scripts with Shellcheck
        uses: essentialkaos/shellcheck-action@v1
        env:
          SHELLCHECK_OPTS: -e SC1117 -e SC2034 -e SC2154
        with:
          files: src/script1.sh src/script2.sh
```

### License

[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

<p align="center"><a href="https://essentialkaos.com"><img src="https://gh.kaos.st/ekgh.svg"/></a></p>
