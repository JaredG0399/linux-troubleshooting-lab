# 26 - Nginx Port Conflict

##Scenario:
- The website was downand nginx was not runnning.

##Investigation:
- The status of the nginx service was checked: "sudo systemctl status nginx".
- The service was not running correctly.
- The configuration was validated: "sudo nginx -t"
- An error was identified indicating that the port 80 was already in use: blind () to 0.0.0.80 failed (address already in use)

##Analysis:
- To identify which proccess was using port 80, the following command was used: "sudo ss -tulpn | grep 80
- The output showed that the Apache service was using port 80
- This created a conlifct , preventing nginx from starting

##Root cause:
- Another service (Apache2) was already using port 80, causing conflict with nginx.

##Resolution:
- The apache service was stopped: "sudo systemctl stop apache2"
- To prevent future conflicts, Apache was disabled: "sudo systemctl disbable apache2"
- Then nginx was started: "sudo systemctl start nginx"

##Verification:
- The nginx service was verified: "sudo systemctl status nginx"
- The service was tested: "curl localhost"
- The service was running correctly and the site was accessible.

##Conclusion:
- Port conclicts can prevent services from starting.
- It is important to identify which process is using a port and manage service properly instead of forcefully terminating proccess.

##Commands used:
- sudo systemctl status nginx
- sudo nginx -t
- sudo ss -tulpn | grep 80
- sudo systemctl stop apache2
- sudo systemctl disabled apache2
- sudo systemctl start nginx
- curl localhost
