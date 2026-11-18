# Network Traffic Analysis and DNS Investigation

I built this project to organize my notes on network traffic analysis, packet inspection, DNS investigation, and network visibility into one structured security portfolio project.

My focus is on understanding what network traffic can show, how I can use Wireshark and tcpdump to inspect it, and where packet-level evidence adds detail that firewall or proxy logs do not provide.

## Project scope

The project is based on my existing Notion notes and one original network capture that I collected and supplied for analysis. It covers:

- Network traffic analysis and the difference between metadata and packet payloads
- Wireshark packet dissection, filtering, stream analysis, and capture statistics
- tcpdump capture and offline packet review
- DNS records, DNS resolution, suspicious DNS queries, and DNS visibility
- TCP flags and connection behaviour
- HTTP request and response inspection, including file extraction concepts
- Visibility limits when traffic uses TLS, SSH, and other secure protocols
- A packet-level review of my supplied PCAPNG capture

## How I have organized the work

| Section | What I cover |
| --- | --- |
| [Project overview](00-project-overview/README.md) | Purpose, scope, and limits |
| [Network fundamentals](01-network-fundamentals/README.md) | Network traffic analysis, visibility, and the TCP/IP layers |
| [Wireshark](02-tools/wireshark.md) | Packet dissection, filters, streams, exports, and statistics |
| [tcpdump](02-tools/tcpdump.md) | Command-line capture, filters, and offline review |
| [DNS investigation](03-dns-investigation/README.md) | DNS log examples, tunneling concepts, and original capture findings |
| [DNS and HTTP fundamentals](03-dns-investigation/dns-http-fundamentals.md) | Domain structure, URLs, HTTP requests, responses, status codes, and headers |
| [TCP traffic analysis](04-tcp-traffic-analysis/README.md) | TCP flags, handshakes, scan signatures, and original capture findings |
| [HTTP file transfer](05-http-file-transfer/README.md) | Proxy metadata, packet payloads, stream reassembly, and original capture findings |
| [Protocol visibility](06-protocol-visibility/README.md) | What I can and cannot inspect in secure protocol traffic |
| [PCAP investigation](08-pcap-investigation/README.md) | Capture details, DNS, TCP, HTTP, findings, and limitations |
| [Reference material](07-reference/README.md) | Filters, commands, and source notes |

## My investigation approach

I start with the information available in the logs or capture. I identify the source and destination, time, protocol, port, and relevant query or request details. I then narrow the traffic with filters and inspect the packet fields or stream where the capture contains that information.

I keep observations separate from conclusions. A suspicious domain, unusual query, or connection pattern can justify further review, but it does not automatically prove compromise, data theft, or command execution.

## Original capture

I reviewed the supplied file at [assets/network-traffic-investigation.pcapng](assets/network-traffic-investigation.pcapng).

The capture contains 10,112 packets over approximately 5 minutes and 22 seconds. It includes DNS, TCP, UDP, ARP, HTTP, and TLS-related traffic. The detailed findings are in [08-pcap-investigation](08-pcap-investigation/README.md).

The capture shows normal DNS resolution and web requests during the recorded period. I did not find DNS TXT queries or an HTTP file transfer matching the ZIP extraction example in my notes. I have not treated the unusual-looking NeverSSL subdomain as malicious because the capture also shows it being resolved and used in an HTTP request to the same service.

## Evidence and project status

The original capture is evidence from my own supplied environment. The investigation reports separate packet observations from interpretation and state what the capture does not prove.

The DNS tunneling and HTTP ZIP download examples elsewhere in this repository remain reference examples from my Notion notes. They are not findings from this capture.

## Reference images

I organized the images from my six Notion pages into the `assets` directory and embedded them in the relevant project documentation.

| Asset folder | Used in | Contents |
| --- | --- | --- |
| [dns-http](assets/dns-http/) | [DNS and HTTP fundamentals](03-dns-investigation/dns-http-fundamentals.md) | Domain structure, URLs, HTTP requests, responses, status codes, and headers |
| [network-traffic-analysis](assets/network-traffic-analysis/) | [Network fundamentals](01-network-fundamentals/README.md) | Network sources, flows, proxy inspection, DNS resolution, and SMB with Kerberos |
| [secure-protocols](assets/secure-protocols/) | [Protocol visibility](06-protocol-visibility/README.md) | HTTP and HTTPS connection flows |
| [tcpdump](assets/tcpdump/) | [tcpdump](02-tools/tcpdump.md) | Commands and capture filter examples |
| [wireshark-traffic-analysis](assets/wireshark-traffic-analysis/) | [TCP, UDP, ICMP, and ARP analysis](04-tcp-traffic-analysis/README.md) | TCP scan, UDP filters, ICMP errors, ARP indicators, and display filters |
| [wireshark](assets/wireshark/) | [Wireshark](02-tools/wireshark.md) | Capture setup, packet inspection, filters, and statistics |

There were 66 uploaded image files. I kept 65 unique images and removed one exact duplicate. These images are reference material from my notes, not proof of a separate incident investigation.

## Source notes

- [Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
- [Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
- [Wireshark Traffic Analysis](https://app.notion.com/p/3edf055fceba80979359e93edc7bb146)
- [tcpdump](https://app.notion.com/p/3c2f055fceba8086af04d794e8b83e17)
- [DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
- [Network Secure Protocols](https://app.notion.com/p/3bbf055fceba80a1a0b3f26ead0c17cd)
- [Incident Detection and Network Monitoring](https://app.notion.com/p/376f055fceba80d5b4bce75293d9bb4b)

## Current status

I have added an original PCAP-based investigation to the documentation. The capture supports DNS, TCP, and HTTP observations. It does not contain evidence for every scenario in my reference notes, so I have documented those gaps instead of filling them with assumed results.
