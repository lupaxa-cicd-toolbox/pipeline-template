<p align="center">
    <a href="https://github.com/lupaxa-cicd-toolbox">
        <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/organisations/cicd-toolbox/readme-logo.png" alt="Organisation Logo" />
    </a>
</p>

<h1 align="center">pipeline-template</h1>

Reusable shell-based CI/CD pipeline template for Lupaxa projects.

## What this is

`src/pipeline.sh` is a single-file, copy-and-configure scanner/linter runner. New
CICD Toolbox tools copy this script and edit only the configuration block at
the top (above `# STOP HERE`).

It is CI-agnostic: the same script runs from GitHub Actions, Bitbucket
Pipelines, Travis CI, or a local shell.

## Quick start

1.   Copy `src/pipeline.sh` into your tool repository.
2.   Edit the **CONFIGURATION** section:
     - package / install / test / version commands
     - file type / name patterns
     - `SCAN_ROOT` default (use `SCAN_ROOT="${SCAN_ROOT:-.}"` so CI can override)
3.   Run it:

```bash
./pipeline.sh
```

### Runtime environment variables

| Variable         | Default        | Meaning                                          |
|------------------|----------------|--------------------------------------------------|
| `REPORT_ONLY`    | `false`        | Report results but always exit 0                 |
| `SHOW_ERRORS`    | `true`         | Print failure details                            |
| `SHOW_FILTERED`  | `false`        | Show excluded paths                              |
| `SHOW_UNMATCHED` | `false`        | Show paths that matched neither pattern          |
| `INCLUDE_FILES`  | *(empty)*      | Comma-separated path regexes to force-include    |
| `EXCLUDE_FILES`  | *(empty)*      | Comma-separated path regexes to skip             |
| `NO_COLOR`       | `false`        | Disable colour output                            |
| `SCAN_ROOT`      | script default | Override scan directory without editing the file |

Example:

```bash
SHOW_ERRORS=true EXCLUDE_FILES='vendor/.*,dist/.*' ./pipeline.sh
```

## Smoke tests

```bash
tests/smoke/run-smoke.sh
```

<a href="https://github.com/the-lupaxa-project">
    <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/components/footer-for-child-orgs.svg" alt="The Lupaxa Project Footer" width="100%" />
</a>
