# HTTP Traffic Investigation

## Objective

I reviewed the HTTP requests and responses in the capture to identify the requested hosts, methods, response codes, content types, and content lengths. I also checked whether the capture contained a file transfer similar to the ZIP example in my network traffic notes.

## Observed HTTP activity

The decoded HTTP packets include these request and response exchanges:

| Frames | Request or response | Host or content |
| --- | --- | --- |
| 2236, 2239 | GET and HTTP 200 | detectportal.firefox.com, /success.txt?ipv4, text/plain, 8 bytes |
| 2335, 2344 | POST and HTTP 200 | ocsp.starfieldtech.com, OCSP request and response |
| 2346, 2356 | POST and HTTP 200 | ocsp.starfieldtech.com, OCSP request and response |
| 5796, 5802 | POST and HTTP 200 | ocsp.r2m04.amazontrust.com, OCSP request and response |
| 5800, 5803 | POST and HTTP 200 | ocsp.r2m04.amazontrust.com, OCSP request and response |
| 9878, 9880 | GET and HTTP 200 | neverssl.com, text/html, 1,900 bytes |
| 10013, 10015 | GET and HTTP 200 | brightsilvermajesticlove.neverssl.com, text/html, 1,900 bytes |

The OCSP requests use the `application/ocsp-request` content type. Their responses use `application/ocsp-response`.

## Notable request

Frame 10013 contains:

```http
GET / HTTP/1.1
Host: brightsilvermajesticlove.neverssl.com
```

Frame 10015 contains an HTTP 200 response. The response content type is `text/html; charset=UTF-8` and the reported content length is 1,900 bytes.

This request matches the hostname observed in the DNS investigation.

## File transfer review

My Notion notes describe an HTTP file download example with a ZIP response and a workflow for following the TCP stream and exporting HTTP objects.

I did not find a request for the example ZIP path or a response with the `application/zip` content type in this capture. The observed HTTP content types are text/plain, text/html, application/ocsp-request, and application/ocsp-response.

I did not extract a file or calculate a file hash because this capture does not show the ZIP transfer described in my notes.

## Interpretation

The HTTP traffic shows browser connectivity activity, certificate status requests, and web page requests. The capture contains successful HTTP responses, but a 200 response does not establish that a file is safe or malicious.

## Limitations

- This review covers HTTP traffic visible in this capture only.
- HTTPS application data remains encrypted in the capture.
- The capture does not provide evidence of the example ZIP download.
- I did not perform malware analysis or submit any file to a sandbox.

## Conclusion

The capture provides examples of HTTP request and response inspection. It does not provide the file transfer evidence needed to demonstrate HTTP object extraction. I have documented that limitation rather than inventing a downloaded file or hash.

## Related notes

[My Notion notes: Network Traffic Analysis](https://app.notion.com/p/3ecf055fceba80bbac9bce5286c10134)
