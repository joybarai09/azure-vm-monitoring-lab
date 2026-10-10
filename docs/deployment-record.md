# Deployment Record

## Verified from Azure portal screenshots and user confirmation

| Item | Verified state |
|---|---|
| Resource group | `rg-azure-monitoring-lab` |
| Region | `East US 2` |
| VM | `vm-monitoring-01` |
| VM availability | Portal showed `Available` |
| Azure Monitor Agent | `AzureMonitorLinuxAgent`, status `Provisioning succeeded`, version `1.45.1` shown |
| Data collection rule | `msvmi-eastus2-vm-monitoring-01` |
| Associated resource | `vm-monitoring-01` |
| Workspace | `defaultazuremonitorworkspace-eus2` |
| Action group | `monitoring-lab-Actiongroup`, one email and one SMS action |
| CPU alert | `alert-vm-monitoring-01-high-cpu`, `Percentage CPU > 80`, enabled |
| Low-memory alert | `alert-vm-monitoring-01-low-memory`, threshold 209715200 bytes, less-than comparison, 1-minute evaluation, 5-minute lookback |
| Notification test | User confirmed both SMS and email were received |
| Dashboard | `VM-Monitoring-Dashboard` |
| Dashboard metrics | CPU average, available memory average, disk read bytes sum |

## Observations

- The dashboard showed approximately 377.89 MiB available memory at the time of the screenshot. This is a time-specific sample, not a current value.
- The disk read chart showed approximately 1.71 GiB for the selected time range in the screenshot.
- CPU usage was mostly low in the displayed 24-hour chart, with a short spike. This is not a performance benchmark.
- The DCR Data sources page showed `Otel Performance Counters` and `Unsupported` under Transform. Review DCR configuration and confirm data is arriving in the intended destination.
- A `Disk Write Bytes` dashboard chart was planned next but was not confirmed as saved.

## Recommended final validation checklist

- [ ] Open each alert rule and verify scope, condition, severity, and action group.
- [ ] Confirm email and SMS recipients are correct without publishing them.
- [ ] Check that metrics continue to arrive after refreshing the dashboard.
- [ ] Verify DCR data sources and destinations; investigate the `Unsupported` transform indication if relevant.
- [ ] Add Disk Write Bytes only if it is available and returns useful data.
- [ ] Capture sanitized screenshots for portfolio evidence.
- [ ] Review Azure Cost Management and stop/delete resources when the lab is no longer needed.
