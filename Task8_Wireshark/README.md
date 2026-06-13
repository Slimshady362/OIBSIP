# Task 8 - Network Traffic Analysis with Wireshark

## Objective

Capture and analyze network traffic using Wireshark.

## Tools Used

* Wireshark
* Npcap

## Procedure

1. Installed Wireshark and Npcap.
2. Selected the active network interface.
3. Started packet capture.
4. Generated network traffic by visiting web pages.
5. Applied the HTTP display filter.
6. Analyzed captured HTTP packets.

## HTTP Packets Observed

### HTTP GET Request

```text
GET /online HTTP/1.1
```

The client requested the `/online` resource from the web server.

### HTTP 301 Moved Permanently

```text
HTTP/1.1 301 Moved Permanently
```

The server redirected the client to a different URL.

### HTTP 200 OK

```text
HTTP/1.1 200 OK
```

The requested resource was successfully returned by the server.

### Favicon Request

```text
GET /favicon.ico HTTP/1.1
```

The browser requested the website's favicon after loading the page.

## Analysis

The capture demonstrated how HTTP communication occurs between a client and a server. Requests and responses were visible in plaintext, including URLs and HTTP status codes.

The analysis showed:

* HTTP GET requests
* HTTP redirects (301)
* Successful responses (200 OK)
* Retrieval of webpage resources

## Security Implications

HTTP traffic is not encrypted. An attacker monitoring the network may be able to view transmitted information.

To protect confidentiality and integrity, HTTPS should be used instead of HTTP whenever possible.

## Files Included

* wireshark_capture.pcap
* screenshots/
* README.md

## Conclusion

Wireshark successfully captured and displayed HTTP traffic on the local network. Packet analysis demonstrated how client-server communication occurs and highlighted the importance of encrypted communications.
