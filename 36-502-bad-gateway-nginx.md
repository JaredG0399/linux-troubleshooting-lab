# 36 - 502 Bad Gateway (socket Mismatch)

##Scenario: 
- The website was returning a "502 bad gateway" error.

##Investigation:
- The service was tested locally: "curl localhost"
- The response returned: 502 Bad Gateway
- This confirmed that nginx was running bue unable to communicate with the backend.

##Analysis:
- The backend service (php-fpm) status was checked: "sudo systemctl status php-fpm"
- The service was running, indicating the issue was not due to the backend being down.
- Logs were reviewed: sudo journalctl -u php-fpm -n 50 --no-pager
- An error related to socket binding ir connection was observed.

##Root cause:
- There was a mismatch between the socket defied in nginx and the one used by php-fpm.
- Nginx was configured to use: "fastcgi_pass unix:/run/php/php7.4-fpm.sock;"
- While php-fpm was using: listen = /run/php/php8.1-fpm.sock
- This mismatch prevented nginx from connecting to the backend.

##Resolution:
- The nginx configuration was updated: "sudo nano /etc/nginx/sites-available/default
- The socket was corrected: fastcgi_pass unix:/run/php/php8.1-fpm.sock;
- The configuration was validated: sudo nginx-t
- Services were restarted: "sudo systemctl restart nginx" "sudo systemctl restart php-fpm"

##Verification:
- The service was testes again: curl localhost
- The response was successful and the 502 error was resolved.

##Conclusion:
- A 502 Bad Gateway error often indicates a communication issue between nginx and the backend service.
- Socket mismatches are a common cause and must be verified in both nginx and php-fpm configurations.

##Commands used:
- curl localhost
- sudo systemctl status php-fpm
- sudo journactl -u php-fpm -n 50 --no-pager
- sudo nano /etc/nginx/sites-available/default
- sudo nano /etc/php/php8.1/fpm/pool.d/www.conf
- sudo nginx -t
- sudo systemctl restart nginx
- sudo systemctl restart php-fpm
