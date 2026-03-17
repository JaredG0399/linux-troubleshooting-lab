# 16 - SSH port conflict troubleshooting

##Scenario:
- A user reported that they coyld not connect to the server via SSH

##Investigation:
- First the SSH service status was checked: Sudo systemctl status ssh
- The output showed that the service was inactive (dead)
- An attempt was made to start the service: sudo systemctl strart ssh
- However, the service failed to start

##Error analysis:
- The service status was checked again to identify the issue: sudo systemctl status ssh
- The error indicated: "Bind to port failed; address was already using port 22"
- This menas another process was already using port 22.

##Identify the issue:
- To find which process was using port 22, the following command was executed:
	-sudo lsof -i :2: the ourput showed a Phyton process using port 22

##Invesrtigation of process:
- THe process was analyzed using:
	-ps -p 5321 -f: It revealed thatr the process was running phyton script that was not supposed to use port 22

##Resolution:
- Since the oricees was not critical, it was terminated: kill 5321
- After freeing the port, the SSH service was started again: sudo systemctl start ssh.

##Verification:
- The service was checked again:
	-sudo systemctl status ssh: The output confirmed that SSH was running successfully.

##Conclusion:
- port conflicts can prevent services from starting.
- It is importa t to identify which process is using a port before taking action.

##Commands used:
- sudo systemctl status ssh
- sudo systemctl start ssh
- sudo lsof -i :22
- ps -p 5321 -f 
- kill 5321
