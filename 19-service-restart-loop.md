# 19 - Service Restrart Loop troubleshooting

##Scenario:
- The web aplication was down even though the server was accessible.

##Investigation:
- The service was checked: 
	-sudo systemctl status nginx: The output showed the service was in a restart loop.

##Error Analysis:
- Logs were checked:
	-journalctl -u nginx -xe: The error indicated a missing configuration file "No such file or directory"

##Root cause:
- The configuration file in /etc/nginx/sites-enabled/ was missing3

##Resolution:
- The symbolic link was recreated: 
	-sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/

##Verification:
- Configuration was tested:
	-sudo nginx -t
- Then the service was started:
	-sudo systemctl strat nginx
- The service returned to normal operation

##Conclusion:
- Missing configuration files can cause services to fail and enter restart loops
- Proper log analysis is a key to identifyng the root cause

##Commands used:
- sudo systemctl status nginx
- journalctl -u nginx -xe
- ls /etc/nginx/sites-enabled/
- sudo ln -s /etc/nginx/sites-avaliable/default /etc/nginx/sites-enabled/
- sudo nginx -t
- sudo systemctl start nginx
