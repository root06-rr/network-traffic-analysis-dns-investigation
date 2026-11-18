# Scope and Limitations

## In scope

This project covers the network analysis topics already present in my notes:

- Capturing and inspecting network traffic
- Network metadata compared with packet payload visibility
- Network flow information and log correlation
- DNS record types and DNS resolution
- DNS tunneling and TXT record abuse concepts
- Wireshark packet dissection, filtering, stream following, and statistics
- tcpdump live capture and offline packet filtering
- TCP flags and connection lifecycle analysis
- HTTP request and response inspection
- File extraction concepts from captured HTTP traffic
- TLS, SSH, and other secure protocol visibility
- Packet-level review of the supplied network capture

## Outside the current scope

I have not included:

- A live enterprise network deployment
- A production SIEM or network monitoring integration
- Malware samples or extracted binaries
- Verified threat intelligence results
- Confirmed compromise or data exfiltration findings
- Tool screenshots or command output that I have not produced

## Evidence available

I reviewed the supplied file at `assets/network-traffic-investigation.pcapng`. The capture contains 10,112 packets and covers approximately 5 minutes and 22 seconds.

The capture supports observations about DNS queries and responses, TCP connection behaviour, HTTP requests and responses, ARP traffic, and visible TLS connection metadata.

## Evidence limitations

A firewall or proxy log can show metadata such as timestamps, IP addresses, ports, domains, query types, HTTP methods, and status codes. It may not contain the full packet payload.

A PCAP can provide packet-level details when the relevant packets were captured. It cannot show traffic that was not present in the capture. Encrypted application payloads also remain unreadable without the required decryption material or an authorized inspection point.

The supplied capture does not contain DNS TXT queries or an HTTP ZIP transfer matching the examples in my notes. I therefore cannot use it to demonstrate DNS TXT command delivery or HTTP object extraction.

## How I describe suspicious activity

I use terms such as suspicious, unusual, or consistent with a technique when the available information supports further investigation.

I reserve stronger conclusions for evidence that supports them. For example, a randomized-looking DNS subdomain alone does not prove DNS tunneling. A TXT query alone does not prove that a command was delivered or executed. A successful HTTP response alone does not prove that a downloaded file was malicious.
