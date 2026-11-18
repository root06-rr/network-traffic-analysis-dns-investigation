# Capture Metadata and Method

## Source

I reviewed the supplied file:

`assets/network-traffic-investigation.pcapng`

The capture is 16,000,212 bytes. Its SHA-256 hash is:

```text
b8b0acb89cc40e78fbc3b17626375555f910d8a990154526aea1df6da666419e
```

## Capture details

| Field | Value |
| --- | --- |
| Packet count | 10,112 |
| Start time | 2026-11-18 17:04:39 UTC |
| End time | 2026-11-18 17:10:01 UTC |
| Duration | 322.15 seconds |
| Interface | eth0 |
| Link type | Ethernet |
| Capture OS metadata | Linux 6.17.10+kali-amd64 |
| Capture application metadata | Dumpcap, Wireshark 4.6.2 |
| Local IPv4 address observed | 192.168.197.130 |
| DNS resolver observed | 192.168.197.2 |

## Packet counts

| Packet type | Count |
| --- | ---: |
| TCP | 5,228 |
| UDP | 4,877 |
| ARP | 7 |
| Total | 10,112 |

## Analysis method

I inspected the PCAPNG packet records and reviewed the Ethernet, IPv4, TCP, UDP, DNS, HTTP, ARP, and TLS ClientHello fields that were present.

I used the packet numbers to connect observations with the original capture. I reviewed DNS queries and responses, TCP flags and connection sequences, HTTP request and response headers, and visible TLS server names.

This report records packet-level observations from the supplied file. It does not claim that I performed a live enterprise investigation or that I used external threat intelligence to classify the destinations.

## Reproducing the review in Wireshark

The Wireshark topics in my notes provide the workflow for packet filtering, packet details, conversations, endpoints, and protocol statistics. I can reopen the supplied capture in Wireshark and use those views to review the same traffic.

The capture should be treated as the evidence source. The examples in the Notion notes remain reference material and are not substituted for packets that are absent from this file.
