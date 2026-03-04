# 04 - SSH Authentication Log Analysis (Brute-Force Simulation)

##Scenario:
- Simulated multiple failed SSH login attempts from host machine to the virtual server.

##Initial Observation:
- Multiple failed password entries appeared in/var/log/auth.log

##Investigation:
- Checked authentication logs
- Identified repeated failed attempts
- Observed source IP addres (10.0.2.2)
- Confirmed no successful unauthorized logins

##Commands used:
- sudo tail -n 20 /var/log/auth.log
- grep "Failed password" /var/log/auth.log
- grep "Accepted" /var/log/auth.log
- grep "Failed password" /var/log/auth.log | wc -l

##Log Analysis
- We found some attempts to login in our server
- the usernames are "Fakeuser1, Fakeuser2 and Fakeuser3"
- All attempts to login was under the IP 10.0.0.2

##Risk Assessment
- Failed attempts do not indicate compromise.
- NO "Accepted" logins from unkown IPs
- Activity likely simulated brute-force attempt.

##Resolution:
- Ensure SSH key authentication only
- Disable password authentication
- Restrict SSH via firewall
- Monitor logs regularly

##Lessons learned
- Brute-force attempts are common
- logs must be analyzed before assuming compromise
- Succeful login entries are more critical then faled attempts
- Defense in depth is essential.
