# TCP Traffic Investigation

## Objective

I reviewed TCP flags, connection attempts, and connection responses to understand how the local host communicated with remote services. I used the TCP flag and handshake concepts from my Wireshark notes.

## Summary

The capture contains 5,228 TCP packets.

| TCP packet type | Count |
| --- | ---: |
| Initial SYN packets | 141 |
| SYN-ACK packets | 95 |
| RST packets | 48 |
| FIN packets | 153 |

The initial SYN count includes repeated transmissions. It should not be treated as a count of unique scan targets.

All initial SYN packets in the capture came from `192.168.197.130`. There were 98 distinct initial SYN connection tuples. I found SYN-ACK responses for 95 of those tuples. Three tuples had no matching SYN-ACK in the capture.

## Repeated connection attempts to one web service

A notable pattern involved repeated SYN packets from `192.168.197.130` to:

```text
34.223.124.45:80
```

I counted 48 SYN packets to this same destination and port across six client source ports:

- 59610
- 59624
- 58382
- 58390
- 37960
- 37976

Two of the connections later received SYN-ACK responses:

| Frame | Packet |
| --- | --- |
| 9876 | SYN-ACK from 34.223.124.45:80 to client port 58382 |
| 9877 | ACK from client port 58382 |
| 9883 | SYN-ACK from 34.223.124.45:80 to client port 58390 |
| 9884 | ACK from client port 58390 |

The packet sequence shows repeated attempts to connect to the same web service. It does not show a sweep across many destination ports.

## Interpretation

Repeated SYN packets can occur when a connection attempt is retransmitted. In this capture, the repeated attempts are concentrated on one destination address and port. I do not have enough evidence to describe this pattern as a TCP port scan.

The capture also contains reset and FIN packets. These flags show connection termination or reset behaviour, but the flags alone do not establish malicious activity.

## Limitations

- Some TCP conversations may have started before the capture began.
- Some connection attempts may continue beyond the capture end.
- A SYN packet without a matching response in this file does not prove that the destination was closed or filtered.
- The capture does not provide evidence of a broad port scan from the local host.

## Conclusion

The capture contains TCP connection activity and repeated connection attempts to a web service. The observed SYN pattern is not enough to confirm a scan. I have kept the packet counts separate from the interpretation.

## Related notes

[My Notion notes: Wireshark Traffic Analysis](https://app.notion.com/p/3edf055fceba80979359e93edc7bb146)
