# 15 - High CPU Troubleshooting

##Scenario:
- A user reported that the server was extremtly slow.

##Investigation:
- System performance was checked using:
	-top: The output showed that CPU usage was very high; A specific process was consuming nealy all CPU resources.

##Process identification:
- The proces was idntified using: 
	-ps -p 4213 -f: It revealed a Phyton script runnning an infinite loop.

##Resolution:
- The process was evaluated and determined to ve not-critical3
- It was stopping using: Kill 4213

##Verification:
- Cpu usage returned to normal after terminating the process.

##Conclusion:
- High CPU usage can significaly impact server performance.
- Identifying and analyzing processes is essential before taking action.

##Commands used:
- top
- ps -p 4213 -f
- kill 4213
