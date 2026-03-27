# 23 - DNS resolution issue

##Scenario:
- The server could reach the internet using IP addresses, but domain names were not resolving.

##Investigation:
- Connectivity was confirmated: ping 8.8.8.8 
- DNS resolution failed: nslook google.com
- The resolver configuration was checked: cat /etc/resolv.conf
- It showed a local resolver (127.0.0.53).
- Resolver status was checked: systemd-resolve --status
- No upstream DNS servers were configured.

##Root cause:
- The local DNS resolver was not configured with a valid external DNS server.

##Resolution:
- A DNS server was configured: resolvectl dns eth0 8.8.8.8 

##Verification:
- DNS resolution was tested: nslookup google.com
- The command returned a valid IP address.

##Conclusion:
- DNS issues can occur even then network connectivity is working.
- Proper resolver configuration is required for domain name resolution.

##Command used:
- ping 8.8.8.8
- nslookup google.com
- cat etcresolv.conf
- systemd-resolve --status
- resolvectl dns eth0 8.8.8.8 


