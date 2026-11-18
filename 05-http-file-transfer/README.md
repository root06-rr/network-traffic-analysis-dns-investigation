# HTTP File Transfer Analysis

## Why I included this topic

My network traffic notes explain the difference between what a web proxy log records and what a packet capture can provide during an HTTP file transfer.

A proxy log may record the request path, host, user agent, response status, content type, and content length. A packet capture may contain the transferred bytes when the relevant traffic was captured and the payload is available.

## Example from my notes

The example request is:

```http
GET /downloads/suspicious_package.zip HTTP/1.1
Host: www.tryhackme.thm
User-Agent: curl/7.85.0
```

The example response includes:

```http
HTTP/1.1 200 OK
Content-Type: application/zip
Content-Length: 10485760
Content-Disposition: attachment; filename="suspicious_package.zip"
```

These are examples in my notes. They are not evidence of a file that I downloaded or extracted.

## What I can learn from the proxy log

The request and response metadata can help identify:

- The requested file path
- The destination host
- The client user agent
- The HTTP response status
- The content type
- The reported content length
- The filename supplied in the response headers

A 200 OK response means the HTTP request succeeded. It does not establish that the file is safe or malicious.

## What a packet capture can add

If the capture contains the complete relevant HTTP exchange, Wireshark can reassemble TCP segments and expose the application data transferred in the stream.

My notes describe the following Wireshark workflow:

1. Open the capture in Wireshark.
2. Review the HTTP request and response.
3. Follow the relevant TCP stream.
4. Open **File** and then **Export Objects**.
5. Select **HTTP**.
6. Review the listed objects and save the relevant file if it is present.

The extracted file can then be examined separately. My notes mention calculating a SHA-256 hash and checking the file with suitable analysis tools. This repository does not contain the example ZIP file or a hash because neither was supplied as evidence.

## Limitations

- The capture must include the relevant transfer.
- Missing packets can affect stream reconstruction.
- HTTPS payloads are encrypted unless the traffic is available through an authorized decryption or inspection method.
- A filename or content type does not prove what a file contains.
- A successful download does not prove that a file is malicious.

## Source

[My Notion notes: Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
