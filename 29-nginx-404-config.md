# 29 - Nginx 404 Configuration Issue

##Scenario:
- The website was not loading, even though the nginx service was running.

##Investigation:
- The response was tested: "curl localhost"
- The result returned: "404 not found"
- This indicated that nginx was running but could not find the requested resource.
- The content directory was checked: " ls -l /var/www/html/
- An index file (index.nginx-debian.html) was present with the correct permission.

##Analysis:
- Since the file existed and permissions were corecrt, the issue was likely related to nginx configuration.
- The configuration file was reviewed: "sudo nano /etc/nginx/sites-enabled/default
- It was found that: 
	-The root directive was pointing to an incorrect directory:
		-root /var/www/example.com
	-The index directive was misconfigured:
		-index index.index.html;

##Root cause:
- Nginx was pointing to the wrong directory and looking for a non-existent index file.

##Resolution:
- The configuration was corrected:
	-root /var/www/html;
	-index index.html index.nginx-debian.html;
- The configuration was validated: "sudo nginx -t"
- Nginx was restarted: "sudo systemctl restart nginx"

##verification:
- The service was tested again: "curl localhost"
- The website loaded correctly.

##Conclusion:
- A 404 error does not always mean the file is missing. It can also be caused by incorrect nginx configuration such as wrong root or index directives.

##Commands used:
- curl localhost
- sudo systemctl status nginx
- ls -l /var/www/html;
- sudo nano /etc/nginx/sites-enabled/default
- sudo nginx -t 
- sudo systemctl restart nginx
