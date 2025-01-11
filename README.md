<h1>Incident Simulation & Analysis with Snort IDS</h1>


<h2>Description</h2>

This project focuses on implementing Snort, an open-source Intrusion Detection System (IDS), to enhance understanding of network security monitoring. The goal is to set up a home lab environment where Snort is deployed and configured to monitor network traffic and detect potential threats. Testing includes generating ICMP traffic and using Nmap for network scanning to simulate common attack scenarios. The project involves configuring Snort rules, analyzing generated alerts, and investigating detected activities to understand Snort's detection capabilities. This hands-on experience demonstrates proficiency in deploying and configuring Snort IDS, simulating basic security events, and performing network traffic analysis for intrusion detection.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Bash</b> 
- <b>Snort IDS</b>
- <b>Nmap</b>
- <b>ICMP</b>
   
<h2>Environments Used </h2>

- <b>Operating System: Debian Linux</b> (via VirtualBox on Windows 11 22H2)
- <b>Network Environment: A home lab network setup to monitor and analyze simulated ICMP and Nmap traffic using Snort IDS</b>
- <b>Development/Testing Tools: Snort IDS, VirtualBox</b>

<h2>Program walk-through:</h2>

<p align="center">
To begin the project, I started by preparing the environment for Snort installation. I first updated the package list on my Debian Linux virtual machine using the commands: sudo apt update & sudo apt upgrade -y. Next, I installed the required dependencies and tools for Snort to function correctly. This included libraries and utilities such as build-essential, libpcap-dev, libpcre3-dev, and libdnet-dev. I installed these by running: sudo apt install -y build-essential libpcap-dev libpcre3-dev libdnet-dev zlib1g-dev. This step ensured that the system was fully prepared for the installation and configuration of Snort in the next steps. : <br/>
<img src="https://i.imgur.com/aOf5YSt.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<img src="https://i.imgur.com/LiYPcSl.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
After setting up the dependencies, I downloaded the latest Snort source code from the official Snort website. Using the wget command, I downloaded the tarball directly to my virtual machine. Once the download was complete, I extracted the tarball using the tar command, which created a directory with the Snort source code. I navigated into the extracted directory and started the compilation process by running the ./configure script to ensure all dependencies were correctly linked. After verifying that the configuration was successful, I compiled the source code with the make command and then installed Snort on the system using sudo make install. :  <br/>
<img src="https://i.imgur.com/olMOi5Z.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<img src="https://i.imgur.com/rCumYJf.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<img src="https://i.imgur.com/nEJ6rpA.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
With Snort successfully installed, I proceeded to verify the installation to ensure everything was set up correctly. I started by running the snort -V command, which displayed the installed version of Snort along with its build details. This confirmed that Snort was properly installed and functioning : <br/>
<img src="https://i.imgur.com/gfQ8667.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
After verifying the Snort installation, I organized the environment by creating directories for Snort's configuration files and logs. I created a directory for storing custom and predefined Snort rules, another for storing log files, and a separate one for dynamic rule files. These directories were set up under /etc/snort/rules, /var/log/snort, and /usr/local/lib/snort_dynamicrules, respectively. Once the directories were created, I adjusted their permissions to ensure Snort could access and use them properly. This step provided a clear and organized structure for managing Snort's configuration files and logs, setting the foundation for efficient monitoring and analysis. :  <br/>
<img src="https://i.imgur.com/WkbTyJv.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
With the directories set up, I proceeded to download the Snort rule set to enable the detection of specific threats. Using the wget command, I downloaded the official Snort rule package from the Snort website. Once the download was complete, I extracted the contents of the tarball using the tar command. This provided access to the predefined rules and configuration files. After extracting the files, I copied the necessary rule files into the /etc/snort/rules directory using the sudo cp command. This ensured that Snort could access and utilize the rules during its operation. By completing this step, I equipped Snort with the rules required to identify and analyze potential network threats effectively. :  <br/>
<img src="https://i.imgur.com/2Z5fbLr.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<img src="https://i.imgur.com/0XMtCKa.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<img src="https://i.imgur.com/zwwLskH.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
To finalize the setup, I copied Snort’s default configuration files from the source directory to the /etc/snort directory. These files included the main configuration file (snort.conf) and other supporting files necessary for Snort’s operation. Using the sudo cp command, I carefully transferred the configuration files from the directory where Snort was installed to the /etc/snort directory. This step ensured that Snort had access to its default configurations in the proper location, allowing me to modify and customize them later as needed. With these files in place, Snort was fully prepared for configuration and testing. :  <br/>
<img src="https://i.imgur.com/NRlFRYk.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
I used Wireshark to review the captured packets and analyze the decrypted data, focusing on the SSL handshake. This allowed me to examine the traffic in various formats, providing a detailed view of the handshake process and encrypted communications. :  <br/>
<img src="https://imgur.com/EsvGkPU.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
<br />
<br />
Observe the decrypted data:  <br/>
<img src="https://imgur.com/e34VzbD.png" height="80%" width="80%" alt="Network Traffic Analysis & Decryption with Logging Tool Steps"/>
</p>
