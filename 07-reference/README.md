# Reference Material

This section collects the filters, commands, and original Notion pages that support the project documentation.

## Wireshark filters

| Purpose | Filter |
| --- | --- |
| All DNS packets | `dns` |
| DNS over UDP port 53 | `udp.port == 53` |
| Packets involving an IP | `ip.addr == 192.168.1.16` |
| TCP packets | `tcp` |
| HTTP packets | `http` |
| ARP packets | `arp` |
| ICMP packets | `icmp` |
| DNS requests | `dns.flags.response == 0` |
| DNS responses | `dns.flags.response == 1` |
| A record queries | `dns.qry.type == 1` |
| HTTP 200 responses | `http.response.code == 200` |
| HTTP GET requests | `http.request.method == "GET"` |
| SYN bit set | `tcp.flags.syn == 1` |

## tcpdump commands

List interfaces:

```bash
sudo tcpdump -D
```

Capture one packet:

```bash
sudo tcpdump -i any -v -c 1
```

Write a capture file:

```bash
sudo tcpdump -i any -w capture.pcap
```

Read a capture:

```bash
tcpdump -r capture.pcap -nn
```

Read traffic involving port 53:

```bash
tcpdump -r capture.pcap "port 53" -nn
```

## Original Notion sources

1. [5. Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
2. [6. Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
3. [7. WireShark: Traffic Analysis](https://app.notion.com/p/3edf055fceba80979359e93edc7bb146)
4. [13. tcpdump](https://app.notion.com/p/3c2f055fceba8086af04d794e8b83e17)
5. [11. Network Secure Protocols](https://app.notion.com/p/3bbf055fceba80a1a0b3f26ead0c17cd)
6. [1. DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
7. [24. Incident Detection and Network Monitoring](https://app.notion.com/p/376f055fceba80d5b4bce75293d9bb4b)

## Documentation note

The content in this repository is based on my Notion notes. The examples are identified as examples where they are not original evidence. I will add PCAP files, screenshots, extracted files, hashes, or tool output only when I have the actual material and can document its source.
