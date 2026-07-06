# suricata-check-action Example

This repository demonstrates how to use the `suricata-check-action` to validate Suricata rules.

## Overview

The `suricata-check-action` is a reusable GitHub Action that runs `suricata-check` to highlight issues in your rulesets.

## Basic Setup

This example includes:
- `suricata.rules`: A sample ruleset to check.
- `suricata-check.ini`: A configuration file for `suricata-check`.

## Usage

To use this action in your own project, add the following workflow to `.github/workflows/suricata-check.yml`:

```yaml
name: Suricata Check

on:
  pull_request:
    branches: ["main", "master"]
  push:
    branches: ["main", "master"]

concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: ${{ github.ref != 'refs/heads/main' }}

jobs:
  suricata-check:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - uses: Koen1999/suricata-check-action@v1.0
```
