# Ransomware Detection Lab

## Project Overview

This project demonstrates how a Security Operations Center (SOC) analyst can detect and investigate ransomware-related activity using Splunk, Sysmon, and Windows event logs.

The lab simulates a ransomware indicator by creating a ransom note artifact (`YOUR_FILES.txt`) and investigates the resulting endpoint telemetry. The activity is analyzed using Splunk and mapped to the MITRE ATT&CK framework.

---

# Lab Environment

* Windows 10 Virtual Machine
* Splunk Enterprise
* Sysmon
* PowerShell
* Atomic Red Team

---

# Objective

The objective of this lab was to:

* Simulate ransomware-related activity.
* Generate Windows endpoint telemetry.
* Detect the activity using Splunk.
* Investigate the executed process.
* Build an investigation timeline.
* Map findings to MITRE ATT&CK.
* Document the investigation.

---

# Attack Simulation

The lab simulated a ransomware indicator by creating a ransom note file named `YOUR_FILES.txt` on the Windows Desktop. This behavior is commonly associated with ransomware families that leave instructions for victims after encrypting files.

The command executed was:

```cmd
echo T1486 - Purelocker Ransom Note > "%USERPROFILE%\Desktop\YOUR_FILES.txt"
```

---

# Detection

## Process Creation

```spl
index=sysmon EventCode=1 Image="*cmd.exe"
```

## Command Line Detection

```spl
index=sysmon EventCode=1 CommandLine="*YOUR_FILES.txt*"
```

## Timeline Investigation

```spl
index=sysmon CommandLine="*YOUR_FILES.txt*"
| table _time User Computer Image ParentImage CommandLine
| sort _time
```

---

# Investigation Findings

The investigation confirmed that `cmd.exe` executed a command to create a ransom note file on the Desktop. Sysmon recorded the process creation event, and Splunk successfully collected the telemetry. The command line provided clear evidence of the simulated ransomware-related behavior.

This activity occurred within a controlled lab environment for detection and investigation purposes.

---

# MITRE ATT&CK Mapping

| Tactic | Technique                 | Technique ID |
| ------ | ------------------------- | ------------ |
| Impact | Data Encrypted for Impact | T1486        |

---

# Skills Demonstrated

* Splunk Log Analysis
* Sysmon Investigation
* Threat Hunting
* Process Analysis
* Command Line Analysis
* Incident Investigation
* MITRE ATT&CK Mapping
* SOC Investigation Workflow

---

# Project Structure

```text
Ransomware-Detection-Lab
├── README.md
├── Screenshots
├── Queries
├── Reports
└── MITRE
```

---

# Lessons Learned

This lab demonstrated how ransomware-related artifacts can be detected through endpoint telemetry. It reinforced the importance of monitoring process creation events and command-line activity, while also showing how Splunk can be used to investigate suspicious behavior and build an incident timeline.

---

# Conclusion

This project successfully simulated a ransomware-related indicator and demonstrated how a SOC analyst can detect, investigate, and document the activity using Sysmon, Splunk, and the MITRE ATT&CK framework.
