# Findings and Limitations

## Findings

### DNS

I observed 149 DNS queries and 149 responses between `192.168.197.130` and `192.168.197.2`. The query types were A, AAAA, and HTTPS. I did not find TXT queries or NXDOMAIN responses.

The hostname `brightsilvermajesticlove.neverssl.com` stands out because of its long subdomain. It also appears in a DNS answer and a matching HTTP GET request. This evidence does not support calling it DNS tunneling or command-and-control activity.

### TCP

I observed 5,228 TCP packets. The capture includes SYN, SYN-ACK, RST, and FIN flags. Repeated SYN packets to `34.223.124.45:80` are concentrated on one destination port. I did not find evidence of a broad port sweep.

### HTTP

I observed HTTP GET and POST requests with successful responses. The requests include browser connectivity checks, OCSP requests, and NeverSSL page requests. I did not find the ZIP file transfer described in my notes.

### ARP

The capture contains seven ARP packets. I did not find conflicting MAC address claims for the same IP address in those packets.

### Encrypted traffic

The capture contains TLS-related traffic. Server names from ClientHello messages are visible, but the encrypted application payload is not available for content inspection in this review.

## What I cannot conclude

This capture does not establish:

- DNS tunneling or DNS data exfiltration
- TXT-based command delivery
- Command execution on the local host
- A confirmed TCP port scan
- A malicious file download
- Malware execution or compromise
- Activity outside the capture window

## Investigation limits

The capture covers approximately 5 minutes and 22 seconds. It represents traffic visible on one interface during that period. It cannot show traffic that was not captured, activity on other network segments, or events outside the recording window.

I did not use external threat intelligence to classify the observed IP addresses or domains. I also did not extract a binary file or perform malware analysis.

## Overall conclusion

This capture gave me packet-level evidence to review DNS resolution, TCP connection behaviour, HTTP requests and responses, ARP traffic, and visible TLS metadata.

The most useful result is not a confirmed attack. It is the ability to separate what I observed from what I could not prove. The capture supports a practical network traffic analysis exercise, but it does not reproduce the DNS tunneling or suspicious ZIP download scenarios in my reference notes.
