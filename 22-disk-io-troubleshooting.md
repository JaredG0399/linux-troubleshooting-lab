# 22 - Disk I/O Troubleshooting

##Scenario:
- The server was slow even though CPU and memory usage were normal

##Investigation:
- Disk performance was analyzed:
	-iostat -o
- A proccess was identified as a non-critical backup job.
- It was consuming significant disk resources and impacting the system performance.

##Resolution:
- The procces was safely terminated
	-kill -15 2345
- This allowed the proccess to exit gracefully without causing data corruption.

##Verification:
- System performance was monitored after termination:
	-iostat
- The I/O wait decreased and system responsiveness improved.

##Conclusion:
- High disk I/O can cause system slowness even when the CPU and memory are normal.
- Identifying and managing disk-intensive processes is critical for system performance.

##Commands used:
- Iostat
- iotop -o 
- ps -p <PID> -f
- kill -15 <PID>
