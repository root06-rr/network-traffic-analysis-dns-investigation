# PCAP Investigation

## Purpose

I used the supplied `network-traffic-investigation.pcapng` file to move this project beyond reference notes and review an original packet capture. I focused on the areas already covered in my Notion material: DNS visibility, TCP connection behaviour, HTTP requests and responses, and the limits of packet-level evidence.

## Capture file

- File: [network-traffic-investigation.pcapng](../assets/network-traffic-investigation.pcapng)
- File size: 16,000,212 bytes
- SHA-256: `b8b0acb89cc40e78fbc3b17626375555f910d8a990154526aea1df6da666419e`
- Packet count: 10,112
- Capture duration: 5 minutes and 22 seconds
- Start: 2026-11-18 17:04:39 UTC
- End: 2026-11-18 17:10:01 UTC
- Capture interface: `eth0`
- Capture environment: Kali Linux `6.17.10+kali-amd64`
- Capture tool metadata: Dumpcap from Wireshark 4.6.2

The capture metadata identifies the local host as `192.168.197.130` and the DNS resolver as `192.168.197.2`.

## Packet summary

| Protocol or packet type | Packets |
| --- | ---: |
| TCP | 5,228 |
| UDP | 4,877 |
| ARP | 7 |
| **Total** | **10,112** |

The capture contains IPv4 packets. DNS responses also contain an IPv6 address record, but that does not mean IPv6 packets were captured.

## Investigation sections

- [Capture metadata and method](capture-metadata.md)
- [DNS investigation](dns-investigation.md)
- [TCP investigation](tcp-investigation.md)
- [HTTP investigation](http-investigation.md)
- [Findings and limitations](conclusions-and-limitations.md)

## Main findings

1. The capture contains 149 DNS queries and 149 DNS responses. The observed query types are A, AAAA, and HTTPS. I did not find TXT queries.
2. The long subdomain under `neverssl.com` also appears in a DNS answer and a matching HTTP request. The capture does not support calling it DNS tunneling or command-and-control activity.
3. TCP traffic contains repeated SYN packets to the same web service. The pattern does not show a broad port sweep.
4. The HTTP traffic includes browser connectivity checks, certificate status requests, and web page requests. I did not find the ZIP file transfer described in my notes.
5. TLS connection metadata is visible, but the encrypted application payload is not available for content inspection in this capture.

## How I handled the evidence

I recorded packet numbers, addresses, ports, DNS record types, HTTP headers, and response codes where they were present in the capture. I did not use the example malicious domains, TXT payloads, or ZIP file from my notes as if they appeared in this capture.

I also kept the capture limitations visible. The results describe this file and its capture window only. They do not establish what happened before or after the recording.

## Source notes

- [Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
- [Wireshark Traffic Analysis](https://app.notion.com/p/3edf055fceba80979359e93edc7bb146)
- [DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
- [Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
