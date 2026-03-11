# 10 - Memory Troubleshoooting

##Scenario:
- A user reported that the server was running slow.

##Investigation:
- System memory usage was analyzed to determinate if memory pressure was causing the issue.

##Commands used:
- free -h
- ps aux --sort=-%mem | head
- top

##Findings:
- The system had 3.8G of total memory 
- No processes were consuming excessive memory 
- CPU usage was also normal

##Diagnosis:
- Memory usage was within normal limits and was not the cause of the performance issue.

##Conlusion:
-When troubleshooting a slow server, system resources such as CPU
and memory must be verified before assuming the cause.

##Lessons Learned:
- High server latency does not always mean resource exhaustion.
- ALways verify CPU, memory, disk and network usage during troubleshoooting.

