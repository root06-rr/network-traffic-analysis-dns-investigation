# DNS Investigation

## Objective

I reviewed the DNS traffic to identify the requesting host, resolver, queried names, record types, response codes, and answer records. I also checked whether the capture contained TXT queries like the DNS tunneling example in my notes.

## Summary

- DNS queries: 149
- DNS responses: 149
- Distinct queried names: 48
- Source host: `192.168.197.130`
- Resolver: `192.168.197.2`
- DNS response code 0: 149 responses
- NXDOMAIN responses: 0
- TXT queries: 0

## Query types

| Query type | Count |
| --- | ---: |
| A | 59 |
| AAAA | 54 |
| HTTPS | 36 |
| TXT | 0 |

The DNS requests in this capture were sent from `192.168.197.130` to `192.168.197.2` over UDP port 53. The responses returned from the resolver to the requesting host.

## Notable query

I reviewed the query for:

```text
brightsilvermajesticlove.neverssl.com
```

Relevant packet sequence:

| Frame | Observation |
| --- | --- |
| 9887 | HTTPS record query for the hostname |
| 9892 | A record query for the hostname |
| 9893 | AAAA record query for the hostname |
| 9897 | AAAA response includes 2600:1f13:37c:1400:ba21:7165:5fc7:736e |
| 9898 | A response includes 34.223.124.45 |

The same hostname appears in an HTTP GET request in frame 10013. The response in frame 10015 is HTTP 200 OK.

## Interpretation

The long subdomain is worth recording because it stands out from the other queried names. However, the packet sequence also shows that the name resolved to an address and was used in an HTTP request to the same service.

I did not find TXT queries, a sequence of encoded TXT answers, or evidence of data being carried in DNS query labels. The capture therefore does not support a finding of DNS tunneling, TXT-based command delivery, or DNS data exfiltration.

The capture does not explain why the long subdomain was used. I have not assigned it a malicious classification.

## What this capture does not show

- DNS TXT queries or TXT response payloads
- A confirmed DNS tunneling pattern
- A confirmed command-and-control channel
- Evidence that data was exfiltrated through DNS
- DNS activity outside the capture period

## Conclusion

The DNS traffic in this capture shows successful DNS resolution from the local host through the configured resolver. The unusual-looking NeverSSL hostname is linked to a matching HTTP request in the same capture. I cannot use this evidence to claim DNS tunneling or malicious DNS activity.

## Related notes

- [Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
- [DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
