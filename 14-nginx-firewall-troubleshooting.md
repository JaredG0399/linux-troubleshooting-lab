# 14 - Nginx Firewall Troubleshooting 

##Scenario:
- A user reported that the website was not accesible from the network.
- The server was running and rechable via SSH, but the webpage could not be accessed from external machine.

##Investigation:
First, the nginx service status was verfied:
sudo systemctl status nginx
The output confirmed that nginx was running.
Next, the web service was tested locally;
curl localhost
the command returned the default nginx HTML page, confirming that the web server was working correctly on the server itself
Since the service worked locally but not externally, the issue was likely related to networking or firewall rules

##Firewall check:
The firewall status was checked using: sudo ufw status
The output showed that port 80 was blocked

##Resolution:
To allow HTTP traffic, the following commands was executed:
sudo ufw allow 80/tcp
After updating the firewall rules, the website became accessible from external clients.

##Conclusion:
Even if a ssrvice is running correctly, firewall rules can prevent external access
Troubleshooting should follow a logical proccess:
	1- Verify the service status
	2- Testh the service locally
	3- Check network and firewall configuration

##Commands used:
- sudo systemctl status nginx
- curl localhost
- sudo ufw status
- sudo ufw allow 80/tcp
