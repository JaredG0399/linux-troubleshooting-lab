# 31 - SSH Connection Failure (Firewall Block)

##Scenario:
- The user was unable to connect to the server vua SSH.

##Investigation:
- The SSH service status was checked: "sudo systemctl status ssh"
- The service was found to be inactive.
- The service was started: "sudo systemctl start ssh"
- The status was verified again: "sudo systemctl status ssh"
- The service was active and running.
- However, the connection issue persisted.

##Analysis:
- Since the service was running, the next step was to verify if SSH was listening on the correct port :
	-sudo ss -tulpn | grep 22
- The output confirmed that SSH was listening on port 22.
- This indicated that the issue was not related to the service itself.
- The firewall status was checked: "sudo ufw status"
- The firewall was active and blocking port 22.

#Root cause:
- The firewall was blocking incoming connections on port 22, preventing SSH access.

##Resolution:
- SSH acess was allowed through the firewall: "sudo ufw allow ssh"

##Verification: 
- The firewall rules were verified: "sudo ufw status"
- Port 22 was now allowed
- The SSH connection was tested: "ssh localhost"
- The connection was successful.

##Conclusion:
- Even if a service is running and listening on the correct port, firewall rules can block access.
- It is important to verify connectivity at the network level when services appear to be functioning correctly.

##Commands used:
- sudo systemctl status ssh
- sudo systemctl start ssh
- sudo ss -tulpn | grep 22
- sudo ufw status 
- sudo ufw allow ssh
- ssh localhost
