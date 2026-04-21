# 35 - Intermittent Web Performance (Backend Dependency Failure)

##Scenario: 
- The website was reported to load intermittently. Sometimes it responded quickly, while other times it was slow or failed

##Investigation:
- THe service wss tested: "curl localhost"
- The response time was inconsistent, confirming an intermittent performance issue.
- System performance was checked: "top"
- The CPU usage was high, mainly caused bu php-fpm processes.
- Disk activity was analyzed: "sudo iotop -o
- The output showed that php-fpm was generating significant disk I/O.

##Analysis:
- Since php-fpm was consuming both CPU and disk resources, logs were reviewed: sudo tail -n 50 /var/log/php-fpm.log
- THe logs showed repeared errors relared to database connection failures.

##Root cause:
- The backend dependency (MySQL) was not functioning correctly, causing php-fpm to repeatedly attempt connections.
- This resulted in:
	-Repeated error loggging
	-High disk I/O
	-Increased CPU usage
	-Intermittent website performance

##Resolution:
- The MySQL service status was checked "sudo systemctl status mysql
- The service was found to be inactive.
- The serviuce was started: sudo systemctl start mysql

##Verification:
- Logs were monitored again: sudo tail -f /var/log/php-fpm.log
- Error messaged stopped repeating.
- System performance improved, and the website became stable.

##Conclusion:
- Intermittent performance issues are often caused by underlying dependencies rather than the main service itself.
- High CPU and disk usage can be symptoms of repeated failures, not the root cause.
- Identifying repeated logs patterns is essential for finding the true source of the problem.

##Commands used:
- Curl localhost
- top
- sudo iotop -o
- sudo tail -n 50 /var/log/php-fpm.log
- sudo systemctl status mysql
- sudo systemctl start mysql.

