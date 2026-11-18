# DNS Log Example Analysis

## Source of the example

This analysis is based on the firewall DNS log example in my Notion page titled Network Traffic Analysis. It is a learning example, not a log collected from my own network.

## Log entries

```text
2025-10-03 09:15:23  SRC=192.168.1.16  QUERY=aj39skdm.malicious-tld.com  QTYPE=A
2025-10-03 09:15:45  SRC=192.168.1.16  QUERY=cmd01.malicious-tld.com     QTYPE=TXT
```

## Field review

| Field | Value | What it tells me |
| --- | --- | --- |
| First timestamp | 2025-10-03 09:15:23 | Time recorded for the first query |
| Second timestamp | 2025-10-03 09:15:45 | Time recorded for the second query |
| Source | 192.168.1.16 | Internal host shown as the source |
| First query | aj39skdm.malicious-tld.com | A domain with a randomized-looking subdomain label |
| First query type | A | IPv4 address record request |
| Second query | cmd01.malicious-tld.com | A second queried name |
| Second query type | TXT | Text record request |

## Observations

- Both entries identify the same source address.
- The queries are 22 seconds apart.
- The first query uses an A record.
- The second query uses a TXT record.
- The first subdomain label appears randomized.
- The second subdomain contains the text cmd01.

## Interpretation

My Notion notes use this example to explain how DNS can be used for outbound data transfer and inbound command delivery.

A long or randomized-looking subdomain can be worth investigating because DNS query names can carry data. TXT records can also contain arbitrary text. These characteristics are not enough on their own to establish malicious activity.

The 22-second gap is the time between the two supplied entries. It is not enough to establish periodic beaconing. I would need a longer sequence of events to assess repetition and timing.

## Additional evidence needed

To take this further, I would need:

- More DNS events from the same source host
- DNS response records, including TXT answer content
- A PCAP containing the relevant DNS queries and responses
- Resolver or firewall context showing the destination resolver
- Endpoint or other security logs that can be correlated with the DNS activity

## Assessment

The supplied entries show two DNS queries from 192.168.1.16. The domain structure and TXT query provide reasons for further review based on the concepts in my notes.

The available example does not independently prove DNS tunneling, data exfiltration, command delivery, or command execution.

## Source

[My Notion notes: Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
