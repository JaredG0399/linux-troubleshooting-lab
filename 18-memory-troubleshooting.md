# 18 - Memory Troubleshooting

##Scenario:
- The server was slow even though CPU usage was normal.

##Investigation:
- Memory was usage was checked:
	-free -h: the output showed that RAM was almost fully used and swap was active
- To identify memory usage by process:
	-ps aux --sort=-%mem | head
- A java process was consuming most of the memory

##Process analysis:
- The process was analyzed using:
	-ps -p 6123 -f: It was identified as a Java application.

##Resolution:
- The process was evaluated and found to be consuming excessive memory.
- A controlled action was taken to stop or restart the service.

##Verification:
- System performance improved after addressing the memory issue.

##Conclusion:
- High memory usage can cause system slowness even when CPU usage is normal.
- It is important to identify processes and evaluate their role before taking action.

##Command used:
- free -h
- ps aux --sort=-%mem | head
- ps -p 6123 -f
