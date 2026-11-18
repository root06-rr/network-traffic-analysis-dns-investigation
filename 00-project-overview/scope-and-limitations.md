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

## Outside the current scope

I have not included:

- A live enterprise network deployment
- A production SIEM or network monitoring integration
- Original PCAP files that were not supplied
- Malware samples or extracted binaries
- Verified threat intelligence results
- Confirmed compromise or data exfiltration findings
- Tool screenshots or command output that I have not produced

## Evidence limitations

A firewall or proxy log can show metadata such as timestamps, IP addresses, ports, domains, query types, HTTP methods, and status codes. It may not contain the full packet payload.

A PCAP can provide packet-level details when the relevant packets were captured. It cannot show traffic that was not present in the capture. Encrypted application payloads also remain unreadable without the required decryption material or an authorized inspection point.

## How I describe suspicious activity

I use terms such as suspicious, unusual, or consistent with a technique when the available information supports further investigation.

I reserve stronger conclusions for evidence that supports them. For example, a randomized-looking DNS subdomain alone does not prove DNS tunneling. A TXT query alone does not prove that a command was delivered or executed. A successful HTTP response alone does not prove that a downloaded file was malicious.
