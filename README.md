<h1><strong>🌐 Network Traffic Analysis of a Vulnerable Web Application</strong></h1>
📌 Overview

This project demonstrates how to analyze live network traffic while interacting with a deliberately vulnerable web application. Using packet capture, we observe how client-server communication occurs and identify potential security weaknesses.

🎯 Objective

Capture and inspect HTTP/TCP traffic

Understand how web requests travel across the network

Identify patterns that may indicate vulnerabilities or insecure communication

<h3><strong>🧪 Lab Environment</strong></h3>

<img width="1876" height="965" alt="wireshark project 1" src="https://github.com/user-attachments/assets/b60c9ca2-ed54-4fdf-a058-bbf8aae7a215" />


Target: Acunetix TestASP Vulnerable Web Application

Network Analyzer: Wireshark

Protocols observed:

TCP

DNS

QUIC (encrypted traffic)

🔍 Key Observations (From Image)
📡 Packet Capture

Source IP: 172.20.10.3 (client machine)

Destination IPs:

52.98.21.34

44.238.29.244

72.145.35.99

📦 Traffic Details

Multiple TCP Keep-Alive packets → persistent connection

TCP ACK / FIN / Retransmission packets observed

DNS queries resolving domain names

QUIC traffic indicating encrypted communication (likely browser traffic)

⚠️ Security Insight

From the web interface:

The application is intentionally vulnerable to:

SQL Injection

Directory Traversal

Other web-based attacks

🚨 Risk Identified

The site is marked “Not Secure” (HTTP)

This means:

Data is transmitted in plain text

Attackers can intercept traffic using tools like Wireshark

🧠 Analysis

HTTP traffic can be inspected easily when not encrypted

TCP retransmissions may indicate:

Network instability

Packet loss

DNS requests reveal external services being contacted

QUIC traffic is encrypted → harder to inspect (modern browser security)

🛠️ Tools Used

Wireshark

Web browser (Chrome/Edge)

Vulnerable test environment

🎯 Outcome

Successfully captured and analyzed live network packets

Identified:

Communication patterns

Protocol usage

Security weaknesses (lack of HTTPS)

Demonstrated how attackers can monitor traffic in insecure environments

🛡️ Key Takeaways

Always use HTTPS to encrypt traffic

Network sniffing tools can expose sensitive data

Vulnerable web apps are useful for security training and testing

Understanding packet flow improves penetration testing skills

<img width="1541" height="930" alt="WIRESHARK PROJECT 2" src="https://github.com/user-attachments/assets/93319e89-32c7-4f55-b492-189a7db79418" />

<h1><strong>🔐 Capturing GET & POST Requests on an Insecure Website (Wireshark)</strong></h1>
📌 Overview

This project demonstrates how to use packet analysis to capture and inspect HTTP GET and POST requests from an insecure web application. Because the site uses HTTP (not HTTPS), sensitive data such as usernames and passwords can be intercepted directly from network traffic.

🎯 Objective

Filter and analyze HTTP traffic

Capture GET and POST requests

Extract sensitive data (e.g., login credentials)

Understand risks of unencrypted communication

🧪 Lab Environment

Target: Acunetix TestASP Vulnerable Web Application

Network Analyzer: Wireshark

Protocol: HTTP (unencrypted)

🚀 Methodology
1. Start Packet Capture

Open Wireshark

Select active network interface (e.g., Wi-Fi)

Begin live capture

2. Apply Filters
🔎 Filter GET Requests
http.request.method == "GET"
🔎 Filter POST Requests
http.request.method == "POST"
🔎 Filter All HTTP Traffic
http
3. Interact with the Web Application

Open the vulnerable site in a browser

Perform actions such as:

Login

Form submission

4. Analyze Packets

Click on a POST request packet

Expand:

Hypertext Transfer Protocol

Look for:

Form data

Parameters like:

username=admin&password=12345
🔍 Key Findings

HTTP requests are transmitted in plain text

Credentials can be directly extracted from:

POST request body

URL parameters (GET requests)

📌 Example Observation
POST /login HTTP/1.1
username=admin&password=admin123
⚠️ Security Implications

No encryption → data interception is trivial

Attackers on the same network can:

Capture credentials

Hijack sessions

Public Wi-Fi networks are especially vulnerable

🛠️ Tools Used

Wireshark

Web browser

Vulnerable test application

🎯 Outcome

Successfully filtered GET and POST requests

Extracted login credentials from captured packets

Demonstrated the danger of using HTTP instead of HTTPS

