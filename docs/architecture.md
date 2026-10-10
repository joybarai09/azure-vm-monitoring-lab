# Architecture and Design Notes

## Goal

Demonstrate practical Azure administration skills through a low-cost, portal-first VM monitoring lab. The project covers monitoring configuration, metric alerting, notification actions, and an operational dashboard.

## Components

| Component | Lab value | Purpose |
|---|---|---|
| Resource group | `rg-azure-monitoring-lab` | Groups lab resources |
| Region | `East US 2` | Single-region deployment |
| Linux VM | `vm-monitoring-01` | Workload being monitored |
| Azure Monitor Agent | `AzureMonitorLinuxAgent` | Guest monitoring agent; provisioning succeeded |
| Data collection rule | `msvmi-eastus2-vm-monitoring-01` | Configures guest data collection |
| Azure Monitor workspace | `defaultazuremonitorworkspace-eus2` | Workspace selected in infrastructure monitoring configuration |
| Action group | `monitoring-lab-Actiongroup` | Email and SMS notifications |
| Dashboard | `VM-Monitoring-Dashboard` | CPU, memory, and disk read metric charts |

## Monitoring paths

Azure platform metrics such as VM CPU are exposed by Azure Monitor. Guest-level operating system metrics depend on the agent and data collection configuration. Check the metric namespace and available tables before assuming a metric is being collected through the same path.

## Design considerations

- Use metric alerts for simple threshold conditions and low-latency evaluation.
- Keep alert thresholds meaningful for the workload. Lab thresholds are examples, not production recommendations.
- Avoid excessive alerting by using an evaluation frequency and lookback window appropriate to the signal.
- Treat phone numbers, email addresses, subscription IDs, and SSH private keys as secrets or sensitive data.
- Delete lab resources when finished if ongoing costs are not desired.
