# 07 - Service Troubleshooting (Nginx)

##Scenario:
 The web site was reported as not loading

##Investigation:
- The Nginx service status was checking using systemctl.

##Command used:
- systemctl status nginx
- sudo systemctl start nginx
- sudo nginx -t 
- journalctl -u nginx
- curl localhost

##Analysis:
- The nginx service can be verified and managed using systemctl
- Configuration validationis done using "nginx -t"
- Logs can be inspected with journalctl.

##Conclusion:
- Service issued can often diagnosed by checking service status and logs.

##Lesson Learned:
- When a service not responding:
	-Check Service status
	-Start or restart the service
	-Validate configuration
	-Review logs
