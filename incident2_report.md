# Incident Report

## Executive Summary

A ransomware-related activity was simulated by creating a ransom note file on the Windows Desktop.

---

## Detection

Splunk detected execution of cmd.exe responsible for creating YOUR_FILES.txt.

---

## Investigation

The analyst reviewed:

- Process creation
- Parent process
- Command line
- User account
- Timeline

The activity was confirmed as a controlled simulation.

---

## MITRE ATT&CK

T1486 – Data Encrypted for Impact

---

## Conclusion

The simulated ransomware indicator was successfully detected and investigated using Splunk and Sysmon.