# 28 - Intermittent Performance Issue

##Scenario:
- The website was reported to be slow and insconsistent.
sometimes it loaded correctly.

##Investigation:
- Initial testing was performed: "curl localhost"
- The response was inconsistent, confirming intermittent behavior.
- Disk performace was analyzed: "sudo iostat -x 1"
- High I/O wait (%wa) was observed, indicating the system was waiting on disk operations.
- To identify the process causing disk usage: "sudo iotop -ao"
- A process named "updatedb" was indentified as consuming high disk write activity.

##Analysis:
- The "updatedb" process is part of the system (mlocate) and is typically scheduled via cron.
- Although not malicious, it was consuming significant disk resources and causing performance degradation

##Root cause:
- A scheduled system process (updatedb) was heavily utilizing disk I/O, causing intermittent slowness

##Resolution:
- The process was safely terminated: sudo kill -15 <PID>
- This allowed the process to stop gracefully without causing data corruption.

##Verification:
- System performance was monitored again "sudo iostat -x 1"
- The I/O was decresead, and the website response became consistent: "curl localhost"

##Prevention:
- The cron job responsible for running updatedb was reviewed:
	- cat /etc/crontab
	- ls /etc/cron.daily/
- The task can be rescheduled to run during off-peak hours to prevent future impact.

##Conclusion:
- Disk I/O can significantly impact system performance even when CPU and memory are normal.
- Identifying and managing scheduled tasks is essential for maintaning system stability.

##Commands used:
- curl localhost
- iostat -x 1
- sudo iotop -ao 
- sudo kill -15 <PID>
- cat /etc/crontab
- ls /etc/cron.daily/
