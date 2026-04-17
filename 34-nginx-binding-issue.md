# 34 - Service Running but not accesible (binding issue)

##Scenario:
- The web service (nginx) was running, but users were unable to access the site from browser.

##Investigation:
- The service status was verified: "sudo systemctl status nginx"
- Nginx was active and running.
- The service was testes locally: "curl localhost"
- The response was successful, confirming that nginx was not working internally

##Analysis:
- Since the service worked locally but not externally, the isue was likely related to network binding.
- The listening ports were checked: "sudo ss -tulpn | grep :80
- The output showed: 127.0.0.1:80
- This indicated that nginx was only listening on the localhost interface.

##Root cause:
- Nginx was bound to 127.0.0.1, which restricts access to local connections only.
- External connection were not allowed.

##Resolution:
- The nginx configuration file was edited: "sudo nano /etc/nginx/sites-available/default
- THr listen directive was corrected.
- listen 127.0.0.1:80; changed to 0.0.0.0:80; or listen 80;
- The configuration was validated: "sudo nginx -t"
- Nginx was restarted: "sudo systemctl restart nginx"

##Verification: 
- The listening interface was verified: "sudo ss -tulpn | grep :80
- The output showed: 0.0.0.0:80
- The site was the accesible externally.

##Conclusion:
- A service can be running correctly but still be inaccessible if it is bound only to the localhost interface.
- Verifying listening addresses is essential when diagnosing connectivity issues.

##Commands used:
- sudo systemctl status nginx
- curl localhost
- sudo ss -tulpn | grep :80
- sudo nano etc/nginx/sites-available/default
- sudo nginx -t
- sudo systemctl restart nginx
