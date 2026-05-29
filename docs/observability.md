# Observability and Monitoring

This document outlines practical examples for building a small security observability and monitoring baseline.

## Metrics and alerts

Use Prometheus to collect metrics from infrastructure and applications. The example file `metrics/prometheus_rules.yml` defines two reference alerts:

- **HighCPUUsage** — triggers when average non-idle CPU activity is above the configured threshold for 5 minutes.
- **SuspiciousLoginAttempts** — triggers when failed-login activity increases above the configured threshold.

These examples are intentionally simple and should be adapted to real telemetry sources, metric names and alert thresholds before operational use.

## Current repository content

The current repository contains:

- `metrics/prometheus_rules.yml` — reference Prometheus alert rules.
- `docs/observability.md` — this guidance document.
- `.github/workflows/ci.yml` — lightweight validation for YAML and documentation references.

## Planned extensions

Future additions may include:

- Grafana dashboard examples.
- Splunk SPL and QRadar AQL query examples.
- Elastic Security examples.
- Deployment notes for Prometheus, Grafana and alert routing.
- Incident-response handoff guidance.

## Security notes

Reference alert rules are not production-ready by default. Before use, teams should:

1. verify metric availability,
2. tune thresholds against normal behaviour,
3. document false-positive expectations,
4. define alert ownership,
5. connect alerts to an incident-response process.
