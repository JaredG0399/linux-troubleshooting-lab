# 03 - Nginx 403 Forbidden (Permission issue)

##Initial investigation:
- The Nginx service was running normally.
However, when executing "curl localhost", the server returned "403 Forbbiden"

##Commands Used:
- sudo systemctl status nginx: for check service
- ls -l /var/www/html: for check permissions
- chmod 644 index.nginx-debian.html: for permisses to owner,group,others
- chown www-data:www-data index.nginx-debian.html: Assign the file to
correct user.
##Findings:
- Nginx works correctly
- With the command curl localhost the service send "403 Forbidden"
- We check the permisses and looks "-rw-------"
- Nginx runs under the user "www-data"
##Diagnosis
- The permisses were restricted to the owner
- The nginx service runs under the user www-data
- Because the file was not readable by www-data, the server returned
"403 Forbidden".

##Resolution:
- First, permission were modified using: 
"chmod 644 inde.nginx-debian.html.
- This allowed read access for group and others
- For a more secure and professional solution, ownership was changed:
"chown www-data:www data index.nginx-debian.html"
- After these changes, "curl localhost" returned to HTML content correctly
##Lessons learned:
- A 403 error, it´s does not always mean the system is broken.
- Always verify the service status before troubleshooting further.
- Check file permissions when the service is active but content is not served
- Avoid using the chmod 777
- Apply the principle of least privilege
- Understand under which user a service runs
