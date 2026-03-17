# 17 - Disk Full Log Troubleshooting

##Scenario: 
- The server was not saving logs and some services were failing.

##Investigation:
- Disk usage was checked: df -h 
- The disk was found to be 100% full.
- To idenitfy which diretory was consuming space: sudo du -sh /* 2>/dev/null
- The /var directory was using most of the space.
- Further investigation: sudo du -sh /var/log/*
- The syslog file was extremely large.

##Resolution:
- The syslog file was cleared safely using: sudo truncate -s 0 /var/log/syslog

##Verification: 
- Disk space was checked again: df -h 
- space was successfully recovered and the system returned to normal.

##Conclusion:
- Log files can grow uncontrollably and fukk up disk space.
- It is important to safely clear logs without deleting them.

##Command used:
- df -h 
- sudo du -sh /* 2>/dev/null
- sudo du sh /var/log/*
- sudo truncate -s 0 /var/log/syslog
