# Burn

Slow Burn — a minimal, patient appsec dashboard.

Live: https://arrojchino.github.io/burn/
Source: https://github.com/arrojchino/burn

Figures shown on the page are illustrative sample data, not live telemetry.

## Features

- Session clock counting toward a two-hour target with a progress bar.
- Severity and coverage cards (findings, high severity, alerts, tools in chain).
- Triage flow: ingest, normalize, rank, verify, report.
- Findings table with application, severity, type and status.
- Single HTML file, inline CSS and a small timer script. No network, no data.

## Verification

Tested in Chromium: the clock ticks every second, the progress bar fills toward the
target, and the cards and table render. All figures are synthetic and local.
