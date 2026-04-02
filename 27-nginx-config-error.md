# 27 - Nginx Configuration Error

##Scenario:
- The website was down after a configuration change.

##Investigation:
- The nginx service status was checked: "sudo systemctl status nginx"
- The configuration was tested: "sudo nginx -t"
- An error was identified:
	-unexpected "}" in /etc/nginx/sites-enabled/default:15

##Analysis:
- The issue was caused by a syntax error in the nginx configuration file.

##Resolution:
- The configuration file was edited: "sudo nano /etc/nginx/sites-enabled/default"
- The syntax error was corrected.
- The configuration was validated again: "sudo nginx -t"
- The service was restarted: "sudo systemctl restart nginx"
- The website was tested: "curl localhost"


##Conclusion:
- Configration errors can prevent services from starting.
- It is important to follow error messages and validate configuratinos before restarting services.

##Commands used:
- sudo systemctl status nginx
- sudo nginx -t
- sudo nano /etc/nginx/sites-enables/default
- sudo systemctl restart nginx
- curl localhost
