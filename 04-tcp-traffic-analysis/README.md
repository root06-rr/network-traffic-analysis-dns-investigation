# TCP Traffic Analysis

## What I cover

My Wireshark traffic analysis notes explain TCP control flags, display filter syntax, the TCP three-way handshake, and packet patterns associated with TCP connection scans.

## TCP flags

The flags covered in my notes include:

| Flag | Decimal weight | Purpose in my notes |
| --- | ---: | --- |
| FIN | 1 | Starts graceful connection termination |
| SYN | 2 | Coordinates sequence numbers to start a connection |
| RST | 4 | Resets or rejects a connection |
| PSH | 8 | Pushes data toward the application |
| ACK | 16 | Acknowledges received data or handshake traffic |
| URG | 32 | Marks urgent data |

## Exact-match and bit-level filters

An exact-match filter checks the aggregate flag value.

Examples:

```text
tcp.flags == 2
tcp.flags == 18
tcp.flags == 20
```

These values represent SYN, SYN plus ACK, and RST plus ACK in the examples from my notes.

A bit-level filter checks whether a particular flag is set, even when other flags are also present.

```text
tcp.flags.syn == 1
```

This matches packets where the SYN bit is set, including both SYN and SYN-ACK packets.

## TCP connection scan examples

My notes compare two scan patterns:

- **TCP Connect Scan:** Completes the three-way handshake before closing the connection.
- **TCP SYN Stealth Scan:** Sends a SYN and, when the target responds with SYN-ACK, terminates the attempt with a reset rather than completing the handshake.

The notes include these example filters:

```text
tcp.flags.syn == 1 and tcp.flags.ack == 0 and tcp.window_size > 1024
```

```text
tcp.flags.syn == 1 and tcp.flags.ack == 0 and tcp.window_size <= 1024
```

These are the signatures described in my notes. I treat them as filters for reviewing traffic, not as a standalone verdict that a scan is malicious.

## How I would review a capture

1. Start with the TCP traffic.
2. Isolate initial SYN packets.
3. Review the source and destination addresses and ports.
4. Follow the packet sequence to see whether the handshake completed.
5. Review resets and connection teardown.
6. Compare repeated connection attempts and their targets.

## Source

[My Notion notes: Wireshark Traffic Analysis](https://app.notion.com/p/3edf055fceba80979359e93edc7bb146)
