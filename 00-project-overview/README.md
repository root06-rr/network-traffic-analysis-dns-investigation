# Project Overview

## Why I created this project

I wanted one place to bring together my notes on network traffic analysis, DNS, Wireshark, tcpdump, and network visibility. I am using this repository to explain how I approach packet-level investigation and how I connect network activity with the information available in logs.

## Main objective

My objective is to understand how network traffic can be captured, filtered, inspected, and used to investigate suspicious communication.

I focus on three areas:

1. Understanding the traffic and the network layers involved.
2. Using packet analysis tools to narrow down and inspect relevant communication.
3. Recording what the available evidence supports, including what remains unknown.

## Topics covered

- Network traffic analysis and deep packet inspection
- Network flow information and log correlation
- DNS records and the DNS resolution process
- DNS tunneling and command-and-control concepts from my notes
- Wireshark packet analysis and display filters
- tcpdump capture and offline review
- TCP flags and scan behaviour
- HTTP request and response inspection
- TLS and secure protocol visibility limits
- Original packet review using my supplied PCAPNG capture

## What this project is not

This repository is not presented as a production network monitoring deployment. It does not claim that I investigated a live organization or handled a real security incident.

The DNS tunneling and HTTP file extraction scenarios in my notes are reference examples. My original capture review is documented separately and does not show those scenarios.

## How I document findings

For each example, I separate:

- **Source material:** The note, log example, or capture being discussed.
- **Observation:** The fields or behaviour shown by that source.
- **Interpretation:** What the observation may indicate.
- **Limitations:** What cannot be confirmed from the available information.

This keeps the documentation clear about the difference between an indicator and a confirmed finding.

## Original capture review

I added a packet-level review of my supplied capture. It contains DNS queries and responses, TCP and UDP communication, HTTP requests, and TLS-related traffic.

The capture did not show DNS TXT queries or the example ZIP file transfer described in my notes. I recorded those as limitations rather than presenting the reference scenarios as observed activity.

See [PCAP Investigation](../08-pcap-investigation/README.md) for the capture details and findings.
