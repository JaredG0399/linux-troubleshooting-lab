# 13 Disk Full Trubleshooting

##Scenario:
The server started behaving abnormally and some services stopped functioning correctly.
One common cause of these issues in Linux system is a full disk.

##Investigaiton:
First, disk usage was checked using:
	-df-h: This command shows the available and used disk space for all mounted filesystems.
Next, the direcotries using the most disk space were identified:
	-sudo du -sh /* 2>dev/null: The/var directory was consuming a large portion of disk space .
Further investiugation showed that log files were growing significantly:
	-sudo du -sh /var/log/*

##Resolution:
Large log files were cleared using: sudo truncate -s 0 /var/log/syslog
After clearing unnecessary logs, disk space became available again.

##Conclusion:
Disk usage should always be checked when servers behave unexpectedly.
Log files are a common cause of disk space.

##Lessons learned:
use "df -h" to check disk usage 
use "du" to identify large directories.
Logs in "/var/log" can grow quickly and should be monitored.

