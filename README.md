<h1>Incident Simulation & Analysis with Snort IDS</h1>


<h2>Description</h2>

This project focuses on implementing Snort, an open-source Intrusion Detection System (IDS), to enhance understanding of network security monitoring. The goal is to set up a home lab environment where Snort is deployed and configured to monitor network traffic and detect potential threats. Testing includes generating ICMP traffic and using Nmap for network scanning to simulate common attack scenarios. The project involves configuring Snort rules, analyzing generated alerts, and investigating detected activities to understand Snort's detection capabilities. This hands-on experience demonstrates proficiency in deploying and configuring Snort IDS, simulating basic security events, and performing network traffic analysis for intrusion detection.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Bash</b> 
- <b>TCPDump</b>
- <b>Wireshark</b>
- <b>Tshark</b>
   
<h2>Environments Used </h2>

- <b>Operating System: Kali Linux</b> (via VirtualBox on Windows 11 22H2)
- <b>Network Environment: Local traffic capture from Google searches</b>
- <b>Development/Testing Tools: Visual Studio Code, VirtualBox</b>

<h2>Program walk-through:</h2>

<p align="center">
In this step, I used the tcpdump command to capture and analyze network traffic to and from google.com. By running sudo tcpdump -c 10 -#XXtttt host google.com, I captured 10 packets, ensuring the data was displayed in both hexadecimal and ASCII formats for detailed examination. The use of high-precision timestamps and packet counters provided clear tracking of the captured traffic, offering a structured view of the interactions with google.com. : <br/>
<img src="https://imgur.com/NIIYMZw.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used tcpdump to capture traffic to and from google.com and saved it to a file named capture.cpap using the -w option. To automate logging, I created a script watchdog.sh that monitored traffic and managed sequential dump files, with each file limited to 100 bytes in size using the -C 1 flag. The script ensured efficient and organized logging of captured data. :  <br/>
<img src="https://imgur.com/xrM9S7u.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I tested the functionality of watchdog.sh to ensure it effectively captured and logged network traffic as intended. This involved running the script, verifying that sequential dump files were created correctly based on the specified size limit, and confirming the captured data was accurate and complete. : <br/>
<img src="https://imgur.com/lcp5j95.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used Wireshark to open and analyze the captured packets in greater detail, utilizing its advanced filtering and highlighting features to identify and examine any encrypted data collected by TCPdump. :  <br/>
<img src="https://imgur.com/DTF5YC3.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I captured the private key used by the browser during an SSL handshake by setting the SSLKEYLOGFILE environment variable to specify the file path for storing private keys. This allowed the browser to log the keys used in SSL encryption. I then switched the host from google.com to nhs.uk to generate more traffic and encrypted data for capture, providing a richer dataset for analysis. :  <br/>
<img src="https://imgur.com/xZVSOJg.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I configured the protocol by setting the TLS Pre-Master Secret log file, enabling the decryption of captured encrypted traffic. This allowed me to analyze the encrypted data in plain text for detailed examination. :  <br/>
<img src="https://imgur.com/59yPtaJ.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
Observe the decrypted data:  <br/>
<img src="https://imgur.com/e34VzbD.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
</p>
