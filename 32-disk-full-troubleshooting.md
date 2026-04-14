# 32 - Disk Full Causing System Issues.

##Scenario:
- The server was reported to be slow, and some services were failing intermittently.

##Investigation:
- Disk usage was checked: "df -h"
- The root file system was found to be at 100% capacity.

##Analysis:
- A full disk can cause multiple issues as:
	-system slowness
	-services failing to write data
	-logs not being recorded 
- To identify the source of disk usage: "sudo du -sh /* 2> dev/null
- The /var directory was found to be consuming most of the space.
- Further inspection was performed: "du -sh /var/log/*
- The syslog file was significantly larger than other log files.

##Root cause:
- The syslog file had grown excessively, consuming most of the avaliable disk space.

##Resolution:
- The log file was safely truncated "sudo truncate -0 /var/log/syslog
- This cleared the file contents without removing the file itself.

##Verification:
- Disk usage was checked again "df -h" 
- THe disk space was succesfully freed, and system performance improved.

##Prevention:
- Logs were reviewed to identify the cayse of excessive growth: "sudo tail -n 50 /var/log/syslog"
- This helps detect repeated error or misconfigured services.
- Log rotation should also be verified to prevent recurrence.

##Conclusion:
- A full disk can lead to widespread system issues. Identifying larfe files and safely reducing their size is critical for restoring system stability.

##Commands used:
- df -h 
- sudo du -sh 2> /dev/null
- du -sh /var/log/*
- sudo truncate -0 /var/log/syslog
- df -h
- sudo tail -n 50 /var/log/syslog 
