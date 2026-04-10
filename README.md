## Project Overview

This project demonstrates Local File Inclusion (LFI) and Remote File Inclusion (RFI) vulnerabilities in web applications.

The lab shows how attackers exploit poor input validation to access sensitive system files and how these vulnerabilities can be mitigated using secure coding practices.

## Lab Details
- Platform: https://tryhackme.com
- Room: https://tryhackme.com/room/fileinc
- Difficulty: Medium

## Objectives
- Exploit file inclusion vulnerabilities
- Perform black-box testing
- Understand real-world attack vectors
- Apply mitigation techniques

## Tools Used
- Burp Suite Community Edition
- Browser Developer Tools
- TryHackMe File Inclusion Lab

## Exploitation Walkthrough
**Step 1: Identify Vulnerability**
- Inspected input fields and URL parameters
<img width="448" height="320" alt="parameters" src="https://github.com/user-attachments/assets/80733d7f-ff12-4537-b6f5-c8d7ce64750f" />

- Discovered improper input validation on the form, I changed the GET Parameters to POST.
-  <img width="1128" height="120" alt="Improper-Input-Validation" src="https://github.com/user-attachments/assets/3cb49363-b44b-4808-8a36-3dd012153230" />

**Step 2: Intercept Traffic**
- Captured POST request using Burp Suite
-  <img width="851" height="186" alt="Burp-intercept" src="https://github.com/user-attachments/assets/bc0e0901-e5e5-4af4-bdf7-85c55515fe74" />
- Analyzed request structure

**Step 3: Exploit LFI**
- Used payload: ../../../../etc/flag2%00 to change the input value on the cookies tab
- <img width="852" height="280" alt="exploit-LFI" src="https://github.com/user-attachments/assets/821df0cf-89d4-4b2b-9de0-29a5c4cc3736" />

**Techniques:**
- Directory Traversal (../)
- Null Byte Injection (%00)
  
**Result:**
- Accessed sensitive system file outside web root
- Successfully displayed file contents
 <img width="852" height="214" alt="File -Contents" src="https://github.com/user-attachments/assets/14eb17c9-b512-40eb-bd35-4535cfc5c60e" />
<img width="1403" height="505" alt="flag-output" src="https://github.com/user-attachments/assets/4830e063-427e-4092-806a-d8b4971a3819" />


## Vulnerability Analysis
Root causes include:
- Poor input validation
- Insecure PHP file handling
- Lack of security testing

## Mitigation Strategies
- Validate and sanitize all user input
- Disable dangerous PHP functions
- Implement file whitelisting
- Use a Web Application Firewall (WAF)
- Disable verbose error messages

## Key Learnings
- Real-world exploitation of LFI/RFI
- Hands-on experience with Burp Suite
- Understanding of directory traversal attacks
- Secure development awareness
