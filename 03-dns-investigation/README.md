# DNS Investigation

## What I am focusing on

I use this section to organize my DNS notes around normal resolution, DNS query visibility, and the ways DNS can be abused for communication or data transfer.

The main concepts I cover are:

- DNS record types such as A, AAAA, CNAME, MX, and TXT
- The DNS resolution process
- Query names, source hosts, timestamps, and query types
- DNS tunneling concepts
- TXT record responses
- The difference between DNS log metadata and packet-level visibility

## DNS resolution

A DNS lookup can involve a local cache, a recursive resolver, root servers, TLD servers, and an authoritative name server. The recursive resolver returns the answer to the client and can cache it according to the record TTL.

My [DNS and HTTP notes](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc) explain the DNS hierarchy and common record types.

## Example from my network traffic notes

The following firewall DNS log entries are examples documented in my Notion notes:

```text
2025-10-03 09:15:23  SRC=192.168.1.16  QUERY=aj39skdm.malicious-tld.com  QTYPE=A
2025-10-03 09:15:45  SRC=192.168.1.16  QUERY=cmd01.malicious-tld.com     QTYPE=TXT
```

My notes discuss the randomized-looking subdomain, the TXT query, and the possibility of DNS tunneling or command-and-control communication.

The entries provide a starting point for analysis. They do not include the full DNS response, a complete query history, or a PCAP. Two timestamps alone do not establish a repeated beacon interval. The log lines also do not show that a command was executed.

## How I review DNS activity

1. Identify the source host and the timestamps.
2. Review the full queried domain names and record types.
3. Check whether the same host makes repeated queries to the same domain or related subdomains.
4. Compare the query pattern with normal DNS activity for that host, where baseline information is available.
5. Review DNS responses in a packet capture if one is available.
6. Correlate the activity with other relevant logs before reaching a conclusion.

## Original PCAP review

I reviewed DNS traffic in [my supplied capture](../assets/network-traffic-investigation.pcapng). It contains 149 DNS queries and 149 responses between `192.168.197.130` and the resolver at `192.168.197.2`.

The observed query types were:

| Query type | Queries |
| --- | ---: |
| A | 59 |
| AAAA | 54 |
| HTTPS | 36 |
| TXT | 0 |

The capture contains 48 distinct queried names. All 149 DNS responses had response code 0. I did not find NXDOMAIN responses or TXT queries in this capture.

One query worth documenting is `brightsilvermajesticlove.neverssl.com`. The A query appears in frame 9892 and the response in frame 9898 returns `34.223.124.45`. The same hostname appears in an HTTP GET request in frame 10013. The server responds with HTTP 200 in frame 10015.

The long subdomain is unusual, but the matching DNS resolution and HTTP request to the same service do not support calling it DNS tunneling or command-and-control activity. The capture does not explain why the subdomain was used.

## What I can and cannot conclude

The capture shows ordinary DNS request and response activity from the recorded host. It provides query names, record types, response codes, and answer records.

I did not observe DNS TXT activity in this capture. I cannot use it to demonstrate TXT-based command delivery or DNS data exfiltration. I also cannot confirm or rule out activity outside the capture period.

## Related investigation

- [Full capture summary](../08-pcap-investigation/README.md)
- [DNS packet findings](../08-pcap-investigation/dns-investigation.md)
- [DNS and HTTP fundamentals](dns-http-fundamentals.md)

## Related notes

- [Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
- [DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
- [Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
