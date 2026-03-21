#  20 - 403 Forbidden Permission Issue.

##Scenario:
- The website was returning a 403 forbidden error.

##Investigation:
- The nginx service was running, so file permission were checked:
	-ls -l /var/www/html: The output showed that only the root user had access to file.

##Root cause:
- The web server (nginx) did not have permission to read the file.

##Resolution:
- Permissions were updated:
	-chmod 644 /var/www/html/index.html
- Direcotry permissions were verified:
	-chmod 755 /var/www/html

##Verification:
- The web sites was tested and returned the expected content.

##Conclusion:
- Incorrect file permission can cause 403 forbidden errors.
- Proper permission management is essential gor web servers.

##Commands used:
- ls -l /var/www/html
- chmod 644 /var/www/html/index.html
- chmod 755 /var/www/html
