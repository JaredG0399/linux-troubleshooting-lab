## 09 - SSH Brute Force Protection

##Scenario:
- Multiple failed SSH login attempts were detected in the system logs.

##Investigation:
- The authentication logs were analyzed to identify repeated failed login attempts.

##Commands used:
- sudo grep "Failed password" /var/log/auth.log
- sudo grep "Failed password" /var/log/auth.log | wc -1

##Findings:
- Several failed SSH login attempts were detected from the same IP address.
- This pattern may indicate a brute force attack.

##Mitigation:
- Fail2ban was installed to automatically detect and block repeated failed logins attempts.

##Commands used for protection:
- sudo apt install FAil2ban -y 
- sudo systemctl status fail2ban
- sudo fail2ban-client status 
- sudo fail2ban-client status sshd

##Conclusion:
-  Fail2ban helps protect Linux servers by automatically blocking IP addresses that generate repeated failed login attempts

##Lesson learned:
- Monitoring authentication logs is essenial for detecting unauhtorized access attempts.
- Fail2ban provides an automated way to mitigate SSH brute force attacks.

