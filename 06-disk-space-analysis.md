# 06- Disk Space Analysis

##Scenario:
- The server disk usage was analyzed to determinate if storage space could ne causing system issue.

##Command used:
- df -h: check total space
- du -h --max-depth=1 /: find big directories
- du -h /var: Investiage specific folders
- du -h /var/log --max-depth=1: check logs

##Investigation:
- Disk usage was checked usinf "df -h"
- the root filesystem was using only 1% of avaliable space.
- Directory usage was analyzed using "du".
- The largest directory was "/usr", which is expected since it contains installed system software
- Log directory usage was also checked

##Conlusion:
- The system has sufficient disk space and no storage-related issues were identified

##Lessons Learned:
When troubleshooting disk space issues:
	- Use "df -h" to check filesystem usage
	- Use "du" to identify large directories
	- check "/var/log" for large log files.
