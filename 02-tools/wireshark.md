# Wireshark

## How I use Wireshark

Wireshark is a packet analyzer that can capture live traffic and inspect PCAP or PCAPNG files. I use it to examine packet headers, protocol fields, and captured payloads.

My notes cover packet capture, packet dissection, packet navigation, filtering, stream analysis, object export, and capture statistics.

The screenshots in this page are the actual image files uploaded from my Wireshark Notion notes. They document the tool and its features. They are not evidence from a single incident investigation.

## 1. Capture setup and interface

I start by identifying the network interface and selecting the right capture options. I also use the main Wireshark interface to review the packet list, packet details, and packet bytes.

![Wireshark traffic sniffing and capture controls](../assets/wireshark/01-traffic-sniffing-control.png)

![Wireshark main interface](../assets/wireshark/02-wireshark-interface.png)

## 2. Packet coloring and capture files

Packet coloring helps me recognize traffic patterns in the packet list. Wireshark also supports merging capture files and reviewing details about a capture before analysis.

![Wireshark packet coloring rules](../assets/wireshark/03-packet-coloring-rules.png)

![Merging PCAP files in Wireshark](../assets/wireshark/04-merging-pcap-files.gif)

![Wireshark capture file properties](../assets/wireshark/05-capture-file-properties.png)

## 3. Packet dissection and navigation

When I select a packet, Wireshark displays its protocol layers and fields. I can move to a packet by number, search packet contents, mark packets, add comments, and export selected packets.

![Wireshark packet dissection layers](../assets/wireshark/06-packet-dissection-layers.png)

![Packet number navigation](../assets/wireshark/07-packet-navigation.png)

![Finding packets in a capture](../assets/wireshark/08-find-packets.png)

![Marking packets for review](../assets/wireshark/09-mark-packets.png)

![Adding packet comments](../assets/wireshark/10-packet-comments.png)

![Exporting selected packets](../assets/wireshark/11-export-packets.png)

## 4. Time display and expert information

I can change how packet timestamps are displayed. Expert Information also helps identify protocol warnings, errors, and other conditions that may need closer review.

![Wireshark time display options](../assets/wireshark/12-time-display-format.png)

![Wireshark Expert Information](../assets/wireshark/13-expert-information.png)

## 5. Packet filtering

I use capture filters to limit what is recorded and display filters to narrow the view of packets already captured. I can build filters through the interface or write expressions directly.

![Wireshark capture and display filter concepts](../assets/wireshark/14-capture-and-display-filters.png)

![Wireshark IP and protocol filters](../assets/wireshark/15-ip-and-protocol-filters.png)

![Wireshark display filter comparison operators](../assets/wireshark/16-display-filter-comparison-operators.png)

### Contains, regular expressions, and set membership

These filter examples show how I can search for text, match patterns, or check whether a field belongs to a defined set.

![Wireshark contains filter examples](../assets/wireshark/17-contains-filter-examples.png)

![Wireshark regular expression filter examples](../assets/wireshark/18-regex-filter-examples.png)

![Wireshark set membership filter examples](../assets/wireshark/19-set-membership-filter-examples.png)

### Case normalization and type conversion

These examples show functions that change field values before comparison. They are useful when matching text with different capitalization or converting a numeric field into a string.

![Wireshark lowercase normalization](../assets/wireshark/20-lowercase-normalization.png)

![Wireshark uppercase normalization](../assets/wireshark/21-uppercase-normalization.png)

![Wireshark string conversion filters](../assets/wireshark/22-string-conversion-filters.png)

### Reusing filters and profiles

I can save filter expressions as bookmarks, add quick-access filter buttons, and use configuration profiles to keep different analysis settings separate.

![Wireshark filter bookmarks](../assets/wireshark/23-filter-bookmarks.png)

![Wireshark display filter buttons](../assets/wireshark/24-filter-buttons.png)

![Wireshark configuration profiles](../assets/wireshark/25-configuration-profiles.png)

## 6. Capture statistics

The Statistics menu gives me a high-level view of the capture. I use it to review protocol distribution, communicating endpoints, conversations, name resolution, and protocol-specific statistics.

![Wireshark statistics overview](../assets/wireshark/26-statistics-overview.png)

![Wireshark protocol hierarchy](../assets/wireshark/27-protocol-hierarchy.png)

![Wireshark conversations statistics](../assets/wireshark/28-conversations.png)

![Wireshark endpoints statistics](../assets/wireshark/29-endpoints.png)

### Name resolution

These views cover global name resolution settings and the name resolution options available in the Endpoints and Conversations windows.

![Global Wireshark name resolution settings](../assets/wireshark/30-global-name-resolution.png)

![Endpoint name resolution options](../assets/wireshark/31-endpoint-name-resolution.png)

![Conversation name resolution options](../assets/wireshark/32-conversation-name-resolution.png)

### IP geolocation and protocol statistics

The following screenshots cover IP geolocation settings and the IPv4, IPv6, DNS, and HTTP statistics views described in my notes.

![Wireshark IP geolocation settings](../assets/wireshark/33-ip-geolocation-settings.png)

![Wireshark IP geolocation limitations](../assets/wireshark/34-ip-geolocation-limitations.png)

![Wireshark IPv4 and IPv6 statistics](../assets/wireshark/35-ipv4-ipv6-statistics.png)

![Wireshark DNS statistics](../assets/wireshark/36-dns-statistics.png)

![Wireshark HTTP statistics](../assets/wireshark/37-http-statistics.png)

## 7. Stream analysis and object export

I can follow a TCP, UDP, or HTTP stream to review a conversation when the required packets are present. For supported protocols, Wireshark can also export objects found in the capture.

Object extraction depends on the traffic being captured and the payload being available. Encrypted application data is not automatically readable.

## Source

[My Notion notes: Wireshark](https://app.notion.com/p/3ecf055fceba80bdaeb4ce807289c751)
