## 08 - High CPU Investigation

##Initial investigation:
- A user reported that the server was running slow.

##Commands used:
- Top: Check CPU usage
- ps aux --sort=%cpu: Indtify procceses using CPU

##Findings:
- CPU udle was around 90%
- No processes were consuming excessive CPU

##Diagnosis:
- The CPU was not the cause of the performance issue.


##Resolution:
- Further investigation should focus on memory usage, disk space, running processes and network connectivity.
- Always verify system resource utilization before assuming the cause of the issue.
