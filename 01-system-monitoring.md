## Initial Investigation: 
To determine the cause, i began by checking the main system resources: CPU, memory, swap usage, load average, and disk usage
These are the most common cuases of performance issues in a Linux server.

## Commands used:
*Top: Check CPU usage and running procceses
*free -h: Check memory and swap usage
*Uptime: check load average
df -h: Check disk space usage

##Findings:
- CPU idle was above 99%, indicating no cpu bottleneck.
- No suspicious processes consuming High CPU.
- Memory usage was within normal range.
- Swap was not in use.
- Load average was very low.
- Disk usage was below critical levels.

##Diagnosis:
The server resources were healthy. There was no indication of CPU, memory, load, or disk preassure.
The issue was not related to system resource usage.

##Resolution:
Since the server resources were normal, the next step would be to investigate network performance or application-level issues

##Lessons Learned:
Not very performance complaint is caused by server resource usage. It is important to systematically verify CPU, memory
load, and disk before assuming the server is the root cause. 
