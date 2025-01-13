# DNS-ICMP-Traffic-Analysis

<h2>Part 1: Summary of the Problem Found in the DNS and ICMP Traffic Log </h2>
The network protocol analyzer logs indicate that port 53, which is commonly used for DNS queries, is unreachable. This issue occurred when a browser attempted to retrieve the IP address for the website www.yummyrecipesforme.com. The following observations were noted in the tcpdump log:

- UDP Protocol Issue: The outgoing UDP packet sent from the client to the DNS server (IP: 203.0.113.2) could not be processed because the destination port (53) was reported as unreachable.
- ICMP Error Message: The ICMP protocol generated an error message: "udp port 53 unreachable," indicating that the DNS server was not listening on port 53 or was otherwise unable to process the UDP packet.
- Repeated Errors: Subsequent retries produced the same error response, confirming that the issue persisted during the observation period.
The most likely issue is that the DNS server at 203.0.113.2 is either misconfigured, offline, or the port is blocked by a firewall or network access control.

<h2>Part 2: Analysis of the Data and Possible Cause of the Incident  </h2>
Time Incident Occurred:

Time Incident Occured:
The incident occurred at 1:24:32 PM, as indicated by the timestamps in the tcpdump logs.

How the IT Team Became Aware of the Incident:
Customers reported being unable to access the client’s website, receiving a "destination port unreachable" error. The IT team attempted to replicate the issue and confirmed the error through network analysis using tcpdump.

Actions Taken by the IT Department:
The IT team captured network traffic using tcpdump to analyze the issue.
They observed the outgoing UDP packets sent to the DNS server and the subsequent ICMP error messages returned.

Key Findings:
Port 53 on the DNS server (203.0.113.2) is not reachable.
The ICMP error messages consistently indicate "udp port 53 unreachable."
This suggests that the DNS server is not accepting traffic on port 53, potentially due to a configuration error, service outage, or firewall rule blocking access.

Likely Cause of the Incident:
The DNS server may have a service misconfiguration or may be offline.
Alternatively, a firewall or network access control may be blocking traffic to port 53.
There is also the possibility of a Denial-of-Service (DoS) attack targeting the DNS server.

<h2>Proposed Solution:</h2>

Immediate Steps:
- Verify the status of the DNS server (IP: 203.0.113.2) and ensure it is online and running correctly.
- Check the server configuration to confirm that the DNS service is listening on port 53.
- Inspect firewall rules and access control lists (ACLs) to ensure port 53 traffic is allowed.
- Perform a vulnerability scan on the DNS server to check for signs of a potential attack.

 Long-Term Steps: 
- Implement monitoring tools to track DNS server availability and alert the IT team to issues proactively.
- Harden the DNS server against potential DoS attacks by enabling rate-limiting and implementing secure access controls.

<h2>Summary</h2>
The root cause of the problem appears to be a failure in the DNS service on port 53, which may be due to a configuration issue, network block, or potential attack. Further investigation and resolution steps are needed to restore normal operations.
