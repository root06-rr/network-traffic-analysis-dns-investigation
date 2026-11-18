# Protocol Visibility

## Purpose

I use this section to keep track of what can be observed when different protocols appear in network traffic. The main point is that packet visibility depends on the protocol, encryption, and what the capture contains.

## DNS

DNS traffic can expose query names, record types, source and destination information, timestamps, and response records when those packets are captured.

My notes cover A, AAAA, CNAME, MX, and TXT records. They also explain the DNS resolution process through recursive resolvers, root servers, TLD servers, and authoritative name servers.

## HTTP and HTTPS

HTTP traffic is not encrypted by default. When the relevant traffic is captured, packet analysis can expose request methods, headers, response codes, and payload data.

HTTPS uses TLS to protect the application data. A packet analyzer can still show connection and TLS metadata, but it cannot normally read the encrypted HTTP content without the required decryption material or an authorized inspection point.

## TLS

My notes describe TLS as providing confidentiality and integrity for communication over an untrusted network. Certificates and certificate authorities are part of the trust process.

For network analysis, I separate visible connection information from the encrypted application payload.

## SSH

My notes identify TCP port 22 as the default SSH port. SSH encrypts remote shell communication and supports password authentication and key-based authentication.

The presence of SSH traffic does not reveal the contents of the encrypted session by itself.

## SMB and Kerberos

My network traffic notes describe SMB file share access using Kerberos authentication. The flow includes obtaining a Ticket Granting Ticket, requesting a service ticket, presenting that ticket to the file server, and establishing an SMB session.

This is protocol-flow reference material. I do not claim to have investigated an SMB or Kerberos PCAP in this repository.

## Analysis limits

I do not assume that a protocol label reveals the full activity inside a session. Encryption, capture location, packet loss, and available logs all affect what I can conclude.

## Sources

- [Network Secure Protocols](https://app.notion.com/p/3bbf055fceba80a1a0b3f26ead0c17cd)
- [DNS and HTTP](https://app.notion.com/p/3b4f055fceba80ac8ca5d0c7ab247bcc)
- [Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
