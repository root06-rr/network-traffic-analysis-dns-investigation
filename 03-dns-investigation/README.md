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

## How I would review this activity

1. Identify the source host and the timestamps.
2. Review the full queried domain names and record types.
3. Check whether the same host makes repeated queries to the same domain or related subdomains.
4. Compare the query pattern with normal DNS activity for that host, where baseline information is available.
5. Review DNS responses in a packet capture if one is available.
6. Correlate the activity with other relevant logs before reaching a conclusion.

## What I can and cannot conclude

The example shows DNS queries from the same internal source address. The query names and record types are worth reviewing in the context described by my notes.

Without the related packet capture, resolver records, baseline, and supporting endpoint evidence, I cannot independently confirm tunneling, data exfiltration, command delivery, or execution.

## Related notes

- [Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
- [DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
- [Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
