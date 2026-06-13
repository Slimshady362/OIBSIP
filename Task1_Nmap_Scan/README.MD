# Basic Network Scanning with Nmap

## Objective

The objective of this task was to perform a network scan using Nmap to identify open ports and running services on a target machine.

## Tools Used

* Nmap 7.98
* Windows Command Prompt

## Target

A local machine on a private network.

## Commands Used

### Basic Scan

```bash
nmap 192.168.56.1
```

### Service Detection Scan

```bash
nmap -sV --version-light 192.168.56.1
```

## Scan Results

| Port  | State | Service      | Version/Details                         |
| ----- | ----- | ------------ | --------------------------------------- |
| 135   | Open  | MSRPC        | Microsoft Windows RPC                   |
| 139   | Open  | NetBIOS-SSN  | Microsoft Windows netbios-ssn           |
| 445   | Open  | Microsoft-DS | SMB File Sharing                        |
| 554   | Open  | RTSP         | RTSP Service Detected                   |
| 2869  | Open  | HTTP         | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 3306  | Open  | MySQL        | MySQL (Unauthorized Access)             |
| 10243 | Open  | HTTP         | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |



## Analysis

### Port 135 (MSRPC)

Used by Windows for Remote Procedure Call communication between services and applications.

### Port 139 (NetBIOS)

Supports legacy Windows file and printer sharing functionality.

### Port 445 (SMB)

Provides file sharing and network resource access. SMB is frequently targeted by malware and ransomware attacks.

### Port 554 (RTSP)

Used for media streaming and video transmission services.

### Port 2869 (ICSLAP)

Associated with Windows service discovery and network communication functions.

### Port 3306 (MySQL)

Default port used by MySQL database servers. Exposed databases may become a security risk if not properly secured.

### Port 10243 (Unknown)

Nmap identified Microsoft HTTPAPI 2.0 on this port. This indicates that a Windows service is exposing an HTTP endpoint. While this may be legitimate system functionality, exposed services should be reviewed to verify their purpose and ensure they do not introduce unnecessary attack surface.

## Conclusion

The Nmap scan successfully identified multiple open ports and services on the target system. The exercise demonstrates how network scanning can be used to understand a system's attack surface and identify potentially exposed services that may require security review.
