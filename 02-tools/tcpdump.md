# tcpdump

## How I use tcpdump

tcpdump is a command-line tool for capturing and inspecting network packets. My notes cover live capture, packet filtering, output control, and reading saved PCAP files.

Live capture usually requires elevated privileges because it accesses network interfaces. Reading an existing capture file does not normally require root privileges.

## Basic commands

List available interfaces:

```bash
sudo tcpdump -D
```

Capture one packet with verbose output:

```bash
sudo tcpdump -i any -v -c 1
```

Capture traffic and write it to a file:

```bash
sudo tcpdump -i any -w capture.pcap
```

Read a saved capture without resolving names:

```bash
tcpdump -r capture.pcap -nn
```

Read DNS-related traffic from a saved capture:

```bash
tcpdump -r capture.pcap "port 53" -nn
```

## Filtering

tcpdump supports filters based on hosts, ports, protocols, and packet properties.

Examples from my notes include:

- Host-based filters to focus on a specific IP address or hostname
- Port-based filters to narrow traffic by transport port
- Protocol filters for IP, IPv6, TCP, UDP, ICMP, and ARP
- Logical operators to combine filter conditions
- Packet length filters using `greater` and `less`

Example of reading packets from one source address and counting the matching lines:

```bash
tcpdump -r traffic.pcap src host 192.168.124.1 -n | wc -l
```

## Live capture and offline review

I separate the capture stage from the review stage.

1. Identify the interface that should be monitored.
2. Choose a capture filter that matches the traffic needed.
3. Save the capture to a PCAP file.
4. Read the file back with tcpdump.
5. Apply narrower filters to inspect the relevant traffic.

The quality of the review depends on what was captured. A filter that is too narrow can exclude traffic that may later be useful.

## Source

[My Notion notes: tcpdump](https://app.notion.com/p/3c2f055fceba8086af04d794e8b83e17)
