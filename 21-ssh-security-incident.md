# 21 - SSH security incident.


##Scenario:
- the server was reported to be behaving strangely, with concerns about possible unauthorized access.

##Investigation:
- Authentication logs were reviewed:
	-less /var/log/auth.log
- Multiple failed login attempts were identifies from a single IP address, indicating a potenital brute-force attack.
- Further analysis revealed a succesful login: "Accepted passworf for user1 from 192.168.1.50"

##Analysis:
- This confirmed that an unauthorized user had gained access to the system.
- Additional investigation steps were performed: 
	-last
	-who
	-cat /home/user1/.bash_history
- These commands helped identify login sessions, active users and commands executed by the compromised account.

##Root cause:
- A brute-force attack succesfully compromised a user account due to weak or exposed credentials.

##Resolution:
- Inmediate actions were taken to secure the system:
	- changed the compromised user password: passwd user1
	- Reviewed SSH authorized keys: cat /home/user1/.ssh/authorized_keys
	- verified system users: cat /etc/passwd
	- installed and enabled faile2ban to prevent further brute-force attempts: s
		-sudo apt install fail2ban
		-sudo systemctl enable fail2ban	
		-sudo systemctl start fail2ban
	- secured SSH configuration: sudo nano /etc/ssh/sshd_config
		-updated settings: "PermitiRootLogins: NO" "PasswordAuthentication: NO"
	- restarted SSH service: sudo systemctl restart ssh

##Verification:
- Confirmed no suspicious active sessions
- verified logs for new unauthorized attempts
- Ensure SSH access was restricted and secured

##Conclusion:
- Unauthorized access was achieved through brute-force attack.
- Proper log analysis and system investigation are critical to identifying security incidents.
- Implementing preventive measures such as fail2ban and securing SSH configuration significantly reduces future risk.

##Commands used:
- less /var/log/auth.log
- grep "Failed password" /var/log/auth.log
- grep "Accepted password" /var/log/auth.log
- last 
- who
- cat /home/user1/.bash_history
- passwd user1
- cat /home/user1/.ssh/unauthorized_keys
- cat /etc/passwd
- sudo apt install fail2ban
- sudo systemctl start fail2ban
- sudo nano /etc/ssh/sshd_config
- sudo systemctl restart ssh
