# 05- Network connectivity troubleshooting

## Scenario:
- The server was tested to verify network connectivity and internet access.

##Initial investigation:
- The following checks were performed to confirm the network configuration and connectivity.

##Commands used:
- ip a: check if we have assigned an ip
- ip route: for check if the server have conextion to internet
- ping -c 4 8.8.8.8: check internet connextion
- ping -c 4 google.com: for check if the server can resolve names of dominious
- curl google.com: check HTML

##Analysis:
- The server had a valid IP address (10.0.2.15) and a default gateway (10.0.2.2).
- Connectivity to external IP addresses was successful.
- DNS resolution was also functioning correctly.
- HTTP requests returned valid responses.

##Conclusion:
- The server has full network connectivity and internet access.

##Lessons Learned:
Network troubleshooting should follow a layered approach:
- Verify IP address
- Verify default gateway
- Test connectivity to external IP
- Verify DNS resolution.
- Test application-level connectivity
