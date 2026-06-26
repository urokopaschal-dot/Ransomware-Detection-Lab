# Splunk Queries

## Process Creation

index=sysmon EventCode=1 Image="*cmd.exe"

---

## Command Line Detection

index=sysmon EventCode=1 CommandLine="*YOUR_FILES.txt*"

---

## Timeline

index=sysmon CommandLine="*YOUR_FILES.txt*"
| table _time User Computer Image ParentImage CommandLine
| sort _time