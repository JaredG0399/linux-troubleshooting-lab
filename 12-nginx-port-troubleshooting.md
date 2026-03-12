# 12 - Nginx Port troubleshooting

##Scenario:
- A user reported that the website was not accessible.
- However, the nginx service appeared to be running.
- This lab demonstrates how to verify if a service is running and listening on the correct port.

##Investigation:
- first, the nginx service status was verified.
- sudo systemctl status nginx.
	- The output showed that the service was active and running.
	- next, open ports were checked using:
- ss -tulpn | grep 80
	- thus confirmed that nginx was listening on port 80

##Service testing:
- to verify that nginx was responding locally, the following command was used:
	- curl localhost
- The server returned the default nginx HTML page, confirming that the web service was functioning.

##Conclusion:
- Even if a service is running. it is importantto verify that correct port is open and that the service responds to request.
- Command like "systemctl", "ss", and "curl" are essential tools for troubleshooting web services 

##Lesson learned:
- Always verify service status.
- Check open ports when diagnosing connectivity issues.
- Use curl to test web services locally.
