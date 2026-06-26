# MITRE ATT&CK Mapping

Technique:
T1486 – Data Encrypted for Impact

Detection Source:

- Sysmon Event ID 1
- Splunk Process Creation Logs

Observation:

The simulated activity created a ransom note artifact using cmd.exe, which was detected through process creation telemetry and command-line analysis.