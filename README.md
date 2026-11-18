# Network Traffic Analysis and DNS Investigation

I built this project to organize my notes on network traffic analysis, packet inspection, DNS investigation, and network visibility into one structured security portfolio project.

My focus is on understanding what network traffic can show, how I can use Wireshark and tcpdump to inspect it, and where packet-level evidence adds detail that firewall or proxy logs do not provide.

## Project scope

The project is based on my existing Notion notes. It covers:

- Network traffic analysis and the difference between metadata and packet payloads
- Wireshark packet dissection, filtering, stream analysis, and capture statistics
- tcpdump capture and offline packet review
- DNS records, DNS resolution, suspicious DNS queries, and DNS visibility
- TCP flags and connection behaviour
- HTTP request and response inspection, including file extraction concepts
- Visibility limits when traffic uses TLS, SSH, and other secure protocols

## How I have organized the work

| Section | What I cover |
| --- | --- |
| [Project overview](00-project-overview/README.md) | Purpose, scope, and limits |
| [Network fundamentals](01-network-fundamentals/README.md) | Network traffic analysis, visibility, and the TCP/IP layers |
| [Wireshark](02-tools/wireshark.md) | Packet dissection, filters, streams, exports, and statistics |
| [tcpdump](02-tools/tcpdump.md) | Command-line capture, filters, and offline review |
| [DNS investigation](03-dns-investigation/README.md) | DNS log example, tunneling concepts, TXT records, and investigation limits |
| [DNS and HTTP fundamentals](03-dns-investigation/dns-http-fundamentals.md) | Domain structure, URLs, HTTP requests, responses, status codes, and headers |
| [TCP traffic analysis](04-tcp-traffic-analysis/README.md) | TCP flags, handshakes, and scan signatures from my notes |
| [HTTP file transfer](05-http-file-transfer/README.md) | Proxy metadata, packet payloads, stream reassembly, and object extraction |
| [Protocol visibility](06-protocol-visibility/README.md) | What I can and cannot inspect in secure protocol traffic |
| [Reference material](07-reference/README.md) | Filters, commands, and source notes |

## My investigation approach

I start with the information available in the logs or capture. I identify the source and destination, time, protocol, port, and relevant query or request details. I then narrow the traffic with filters and inspect the packet fields or stream where the capture contains that information.

I keep observations separate from conclusions. A suspicious domain, unusual query, or connection pattern can justify further review, but it does not automatically prove compromise, data theft, or command execution.

## Evidence and project status

The examples currently documented here come from my Notion learning notes. They are reference examples, not a claim that I captured or investigated the underlying traffic myself.

I have not added fabricated PCAP files, packet screenshots, extracted binaries, hashes, or tool output. When I add original capture evidence, I will document the source and connect each finding to the relevant packet or log record.

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

There were 66 uploaded image files. I kept 65 unique images and removed one exact duplicate. Every remaining image is embedded in a project Markdown file. These images are reference material from my notes, not proof of a separate incident investigation.

## Source notes

- [Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
- [Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
- [Wireshark Traffic Analysis](https://app.notion.com/p/3edf055fceba80979359e93edc7bb146)
- [tcpdump](https://app.notion.com/p/3c2f055fceba8086af04d794e8b83e17)
- [DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
- [Network Secure Protocols](https://app.notion.com/p/3bbf055fceba80a1a0b3f26ead0c17cd)
- [Incident Detection and Network Monitoring](https://app.notion.com/p/376f055fceba80d5b4bce75293d9bb4b)

## Current status

This repository is the organized documentation stage of my network traffic analysis work. The next step is to add original PCAP-based exercises and record the actual observations only when I have the capture files and supporting evidence.
