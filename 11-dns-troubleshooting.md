# 11 - DNS Troubleshooting

##Scenario:
- The server was able to reach external IP addresses but initially had DNS configuration changes that affected domain resolution.
- This lab demonstrates how DNS resolution works and how to troubleshooting DNS-related connectivity issues.

##Investigation:
- First, network connectivity was veryfie by pinging and external IP address.

##Commands used:
- Ping 8.8.8.8
- Ping google.com
- resolvectl status

#### Troubleshooting Simulation

To simulate a DNS issue, the DNS server was temporarily changed using:

sudo resolvectl dns enp0s3 1.2.3.4

After this change, domain resolution failed because the DNS server was invalid.

This reproduced a common real-world issue where DNS servers are misconfigured.

## Resolution

The DNS configuration was corrected by setting a valid DNS server:

sudo resolvectl dns enp0s3 75.75.75.75

After restoring a valid DNS server, domain resolution worked again.

## Conclusion

When a server can reach external IP addresses but cannot resolve domain names, the problem is usually related to DNS configuration.

Tools such as `ping`, `resolvectl`, and network diagnostics help identify and resolve these issues.

## Lessons Learned

DNS translates domain names into IP addresses.

Troubleshooting DNS issues requires verifying network connectivity first
 then checking DNS configuration and resolution services.
