# 30 - 502 Bad Gateway (Backend failure)

##Scenario:
- The website was returning 502 bad gateway error.

##Investigation:
- The response was tested: "curl localhost"
- The results returned: 502 Bad gateway
- This indicated that nginx was running but could not communciate with the backend service.
- The backend service was checked: "sudo systemctl status php-fpm
- The service was found to be in a failed state.

##Analysis:
- A 502 error tipically indicates that nginx cannot reach or communicate with the backend service.

##Root cause:
- The backend service (php-fpm) was not running.

##Resolution:
- The backend service was restarted: "sudo systemctl restart php-fpm"

##Verification:
- The backend status was confirmed: "sudo systemctl status php-fpm"
- The website was tested again: "curl localhost"
- The error was resolved and the site responded correctly.

##Prevention:
- To indentify the root cause of the failure, logs were reviewed: 
	-sudo journalctl -u php-fpm --no-pager -n 50
- This helps determinate if the issue was caused by memory, crashes. or configuration errors.

##Conclusion:
- A 502 error usually indicates a backend failure rather than an issue with nginx itself.

##Commands used:
- curl localhost
- sudo systemctl status php-fpm
- sudo systemctl restart php-fpm
- sudo journalctl -u php-fpm --no-pager -n 50
