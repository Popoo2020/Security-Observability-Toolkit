# Observability and Monitoring

This document outlines best practices and examples for building an effective security observability and monitoring stack.

## Metrics and Alerts

Use Prometheus to collect metrics from your infrastructure and applications. The example `metrics/prometheus_rules.yml` defines two alerts:

- **HighCPUUsage**: triggers when average CPU usage is above 90% for 5 minutes across nodes.
- **SuspiciousLoginAttempts**: triggers when more than 5 failed login attempts are observed in a 10-minute window.

Prometheus scrapes metrics from exporters and evaluates rules to generate alerts. You can load these rules into Prometheus and integrate alert notifications with Alertmanager.

## Dashboards

Grafana can visualize Prometheus metrics. The `dashboards/grafana/sample_dashboard.json` contains a simple dashboard with two panels:

- **CPU Usage**: graphs average CPU usage over time.
- **Failed Login Attempts**: graphs increases in failed login events.

Import this JSON into Grafana to create a dashboard. Update the datasource name if your Prometheus datasource is named differently.

## Detection Queries

Beyond metrics, log-based analytics are essential. The `detections/` folder contains example queries for Splunk and QRadar:

- **splunk/suspicious_login.spl**: identifies users or IPs with more than 5 failed login attempts.
- **qradar/suspicious_login.aql**: detects the same pattern using QRadar's AQL syntax.

You can adapt these queries to your environment and incorporate them into correlation rules or search templates.

## Extending the Toolkit

This repository provides a starting point. Consider adding:

- Additional Prometheus rules and Grafana panels for network traffic, error rates, or custom application metrics.
- Detection queries for other SIEM platforms such as Elastic Security.
- Integration instructions for exporting metrics and logs from your applications and infrastructure.
- Automated deployment scripts (e.g., Helm charts, Terraform modules).

We welcome contributions! Please follow the `CONTRIBUTING.md` guidelines in the root of your portfolio.
