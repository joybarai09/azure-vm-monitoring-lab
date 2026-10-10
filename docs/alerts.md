# Alert Rules and Notifications

## CPU alert

- Name: `alert-vm-monitoring-01-high-cpu`
- Signal: `Percentage CPU`
- Aggregation: Average
- Operator: Greater than
- Threshold: 80%
- Evaluation frequency: 1 minute
- Lookback period: 5 minutes
- Status: Enabled in the portal screenshot
- Severity: Informational in the alert rules list
- Action group: `monitoring-lab-Actiongroup`

## Low-memory alert

- Name: `alert-vm-monitoring-01-low-memory`
- Signal: `Available Memory Bytes`
- Aggregation: Average
- Operator: Less than
- Threshold: `209715200` bytes (200 MiB)
- Evaluation frequency: 1 minute
- Lookback period: 5 minutes
- Severity: Warning
- Action group: `monitoring-lab-Actiongroup`
- Description shown in the portal: `when available memory falls below 200 MiB for 5 minutes`

## Action group

`monitoring-lab-Actiongroup` was shown with:
- 1 email action
- 1 SMS action

The user confirmed that both the email and SMS notifications were received.

## Operational caution

A memory threshold of 200 MiB is specific to this small lab VM and should not be copied blindly into production. Choose thresholds based on workload behavior, memory capacity, and expected baseline. Confirm the alert fires and resolves as expected, and make sure notification recipients are maintained.
