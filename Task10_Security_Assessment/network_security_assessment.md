# Network Security Assessment Report

## Executive Summary

As part of this assessment, a local system was analyzed using Nmap and Wireshark to gain visibility into exposed network services and observe network communication. The objective was not to exploit vulnerabilities but to understand the system's attack surface and identify potential areas that may require security attention.

The assessment identified several open ports, including services related to Windows networking and a MySQL database service. In addition, HTTP traffic was captured and analyzed to understand how data is transmitted across the network.

---

## Scope of Assessment

This assessment was conducted in a controlled local environment and focused on:

* Identifying open ports and active services
* Analyzing network traffic
* Evaluating potential security risks
* Recommending basic security improvements

No intrusive testing or exploitation was performed during this assessment.

---

## Tools Used

### Nmap

Nmap was used to discover open ports and identify services running on the target machine.

### Wireshark

Wireshark was used to capture and analyze network packets, with a focus on HTTP traffic.

---

## Nmap Scan Findings

The following services were identified during the scan:

| Port  | Service      | Description                     |
| ----- | ------------ | ------------------------------- |
| 135   | MSRPC        | Microsoft Remote Procedure Call |
| 139   | NetBIOS-SSN  | Windows networking service      |
| 445   | Microsoft-DS | SMB file sharing service        |
| 554   | RTSP         | Streaming protocol service      |
| 2869  | HTTP         | Microsoft HTTPAPI service       |
| 3306  | MySQL        | Database service                |
| 10243 | HTTP         | Microsoft HTTPAPI service       |

### Observations

The scan revealed that the system exposes several network services. Some of these services are expected on Windows systems, while others may require additional review depending on the environment and business requirements.

The presence of a MySQL service indicates that a database server is running and accepting network connections. Database services often contain valuable information and should be carefully secured.

---

## Traffic Analysis Findings

Network traffic was captured using Wireshark and filtered to display HTTP packets.

During the analysis, the following events were observed:

* HTTP GET requests
* HTTP redirects (301 Moved Permanently)
* Successful server responses (200 OK)
* Browser requests for additional resources such as favicon files

Example traffic included:

```text
GET /online HTTP/1.1
HTTP/1.1 301 Moved Permanently
HTTP/1.1 200 OK
GET /favicon.ico HTTP/1.1
```

### Observations

The captured packets demonstrated normal client-server communication over HTTP. Because HTTP is not encrypted, request information and response details were visible in plaintext within the packet capture.

This highlights the importance of encrypted communication protocols such as HTTPS, especially when transmitting sensitive information.

---

## Security Analysis

### SMB Service Exposure (Port 445)

Port 445 was found to be open and running the SMB service.

SMB is commonly used for file sharing and resource access within Windows environments. While it is an important service, it has historically been targeted by malware and ransomware campaigns due to its widespread use.

**Recommendation:**

* Restrict SMB access to trusted systems.
* Keep Windows systems updated with security patches.
* Disable SMB if it is not required.

---

### MySQL Database Service (Port 3306)

The scan detected a MySQL service listening on port 3306.

Databases are often high-value targets because they may contain sensitive or business-critical information. Although the service did not allow unauthorized access during scanning, it should still be properly secured.

**Recommendation:**

* Use strong passwords.
* Restrict database access to authorized hosts.
* Regularly update the database software.

---

### Unencrypted HTTP Traffic

The packet capture showed that HTTP traffic could be viewed directly within Wireshark.

An attacker with access to the same network could potentially inspect unencrypted communications and gather information about user activity.

**Recommendation:**

* Use HTTPS whenever possible.
* Avoid transmitting sensitive information over HTTP.
* Implement encryption for web-based services.

---

### General Service Exposure

Multiple network services were exposed on the target system.

Every exposed service increases the system's attack surface and represents a potential entry point that should be monitored and managed.

**Recommendation:**

* Review open ports regularly.
* Disable unnecessary services.
* Perform periodic security assessments.

---

## Recommendations

Based on the assessment, the following actions are recommended:

1. Perform regular network scans to identify exposed services.
2. Keep operating systems and applications updated.
3. Use HTTPS instead of HTTP for web communication.
4. Restrict access to sensitive services such as SMB and MySQL.
5. Monitor network activity for unusual behavior.
6. Review firewall rules and remove unnecessary exposures.

---

## Conclusion

This assessment provided visibility into the network services running on the target system and demonstrated how packet analysis can be used to understand network communication. The findings did not indicate active compromise; however, several exposed services and the presence of unencrypted HTTP traffic highlight areas that should be reviewed as part of a broader security strategy.

Regular assessments, proper service management, and secure communication practices can significantly improve the overall security posture of a system.
