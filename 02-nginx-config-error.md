# 02 - Nginx Configuration Error (Sintaxis issue)

##Initial investigation: 
After modifying the nginx configuration file, the service stopped working
When attempting to restart Nginx,the services failed to strart.

##Commands Used:
- sudo systemctl status nginx: check service status
- sudo nginx -t : validate configuration sintax
- sudo nano /etc/nginx/... : edit configuration file
- sudo systemctl restart nginx: Restart service.

##Findings:
- The nginx service was in a failed state
- The error message indicated that the service attempted to start but exited with an error.
- Running "sudo nginx -t" revealed a sintax error in the configuration fiel caused by a missing semicolon (;)

##Diagnosis
- Missing semicolon (;) in configuration file.
- Nginx cannot strat if configuration sintax is invalid.
- Restarting the service without validation does not resolve configuration errors.

##Resolution: 
- Added the missing semicolon in the configuration file
- Validated configuration again using "sudo nginx -t".
- After confirming "sintax is ok" and "test is successful", the service was restarted successfully.

##Lessons learned:
- Always validate configuration before restarting the service.
- using "sudo nginx -t" helps prevent downtime caused by sintax errors.
- Even small mistakes, such as a missing semicolon, can prevent crittical services from starting.
