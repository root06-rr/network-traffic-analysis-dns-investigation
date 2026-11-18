# Wireshark

## How I use Wireshark

Wireshark is a packet analyzer that can capture live traffic and inspect PCAP or PCAPNG files. I use it to examine packet headers, protocol fields, and captured payloads.

My notes cover packet dissection, packet navigation, filtering, stream analysis, object export, and capture statistics.

## Packet dissection

When I select a packet in the packet list, Wireshark displays the protocol details for that frame. Selecting a field in the packet details also highlights the related bytes in the packet bytes pane.

This helps me move from a packet summary to the specific fields that make up the packet.

## Capture filters and display filters

I keep the difference clear:

- **Capture filters** are set before capture. They decide which packets are recorded.
- **Display filters** are applied after capture. They change which recorded packets are shown without removing the other packets from the capture file.

## Useful display filters from my notes

| Purpose | Filter |
| --- | --- |
| DNS traffic | `dns` |
| UDP traffic involving port 53 | `udp.port == 53` |
| Traffic involving an IP address | `ip.addr == 192.168.1.16` |
| TCP traffic | `tcp` |
| Unencrypted HTTP traffic | `http` |
| ARP traffic | `arp` |
| ICMP traffic | `icmp` |
| DNS queries only | `dns.flags.response == 0` |
| DNS responses only | `dns.flags.response == 1` |
| DNS A record queries | `dns.qry.type == 1` |
| HTTP responses with status 200 | `http.response.code == 200` |
| HTTP GET requests | `http.request.method == "GET"` |

The filter `ip.addr` matches an address in either direction. The fields `ip.src` and `ip.dst` let me narrow the direction.

## Following a stream

The Follow Stream feature reconstructs the application data exchanged within a TCP, UDP, or HTTP stream when the required data is present in the capture.

It is useful when I need to review a conversation instead of reading individual packets in isolation.

## Exporting objects

My notes describe the Wireshark path:

1. Open **File**.
2. Select **Export Objects**.
3. Choose the relevant protocol, such as HTTP or SMB.
4. Review the available files, content types, and hostnames.
5. Select an object and save it for further analysis.

Object extraction depends on the relevant transfer being present in the capture and supported by the protocol dissector. An encrypted stream does not automatically expose its application files.

## Capture statistics

The Statistics menu helps me get an overview of an unfamiliar capture.

The sections in my notes include:

- **Resolved Addresses:** Shows IP addresses mapped to hostnames using DNS answers present in the capture.
- **Protocol Hierarchy:** Summarizes protocols and their packet or byte counts.
- **Conversations and endpoints:** Help identify systems communicating in the capture.

I use these views to decide where to focus next. They are starting points for investigation, not proof of malicious activity.

## Source

[My Notion notes: Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
