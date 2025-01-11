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

<h2>Project walk-through:</h2>

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
To manage my own custom rules for Snort, I created a dedicated local directory. Instead of adding customized rules to the Snort community rules, this approach kept my custom rules separate and organized. Using the mkdir command, I created a directory named local.rules within the /etc/snort/rules folder. This structure allowed me to easily manage and edit my personalized rules without interfering with the predefined rule sets. By keeping my custom rules in a separate directory, I maintained a clear distinction between the community-provided rules and the ones I tailored for specific scenarios in my project. This setup ensured flexibility and organization for managing rule configurations. :  <br/>
<img src="https://i.imgur.com/FBf95xl.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
To create a custom rule for detecting ICMP traffic, I opened the local.rules file located in the /etc/snort/rules directory. Using the nano text editor, I added a rule that would generate an alert for any ICMP traffic, regardless of its source or destination. The rule included a custom message, "ICMP Detected," to clearly indicate the type of traffic being flagged. After saving the file, I ensured the Snort configuration referenced the local.rules file, allowing this custom rule to be applied during traffic monitoring. This step demonstrated Snort’s capability to support tailored detection rules. :  <br/>
<img src="https://i.imgur.com/Am5C7YZ.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
To configure Snort for my specific network environment, I opened the snort.lua configuration file using the nano text editor. I accessed the file with the following command: sudo nano /etc/snort/snort.lua. Within the configuration file, I located the section for setting network variables. I focused on the HOME_NET variable, which defines the range of IP addresses Snort considers part of the local network. I updated this variable to match my home lab’s local network by specifying the appropriate IP range. After saving the changes, this configuration ensured that Snort accurately monitored traffic for my designated local network, enabling precise and targeted intrusion detection.
 :  <br/>
<img src="https://i.imgur.com/VMqJ4wA.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
While editing the snort.lua configuration file, I added the paths to both the Snort community rules and my custom local rules. These rules enable Snort to detect predefined threats and any custom conditions I specified. In the configuration file, I located the section where rule files are included and added entries for the Snort community rules and the local.rules file. This ensured that Snort would load and apply both rule sets during operation. After saving the updated configuration, Snort was configured to use a combination of community-provided and custom rules, enabling comprehensive and tailored traffic monitoring for my project. :  <br/>
<img src="https://i.imgur.com/PDyhNVO.png" IDS Steps"/>
<br />
<br />
After updating the Snort configuration file, I saved the changes and closed the file. To ensure that the configuration was valid and free of errors, I tested it using Snort's test mode. I ran the following command to specify the configuration file and verify its correctness: snort -T -c /etc/snort/snort.lua. This command checked the configuration for any syntax errors or issues. The output confirmed that the configuration was successfully loaded and ready for use. This step ensured that Snort was properly set up and prepared for monitoring and analysis.
 :  <br/>
<img src="https://i.imgur.com/jl2iFx0.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<img src="https://i.imgur.com/VYOH6VN.png" height="80%" width="80%" alt="IDS Steps"/>
<br /r>
<br />
With the configuration validated, I proceeded to run Snort in Intrusion Detection System (IDS) mode. Using the following command, I started Snort to monitor traffic on my specified network interface (eth0):snort -A fast -q -c /etc/snort/snort.lua -i eth0. In this mode, Snort operated quietly (-q) while logging alerts in a simplified format (-A fast). It used the configuration file located at /etc/snort/snort.lua and monitored the eth0 interface for suspicious activity. This step activated Snort as an IDS, enabling real-time detection and logging of network events based on the configured rules and settings. :  <br/>
<img src="https://i.imgur.com/cmOq8Y1.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
To test the Snort IDS, I initiated Nmap scans from another machine on the network to generate traffic. These scans were designed to simulate potential reconnaissance activity, which Snort was configured to detect. While the scans were running, I monitored the logs generated by Snort using the following command: sudo tail -f /var/log/snort/alert_fast.log. This allowed me to view alerts in real time as Snort detected and logged the activity. The logs confirmed that Snort successfully identified and recorded the Nmap scan traffic, demonstrating its functionality as an intrusion detection system.
:  <br/>
<img src="https://i.imgur.com/IIHtuNG.png" height="80%" width="80%" alt="IDS Steps"/>
<br />
<br />
<h2>Project Summary:</h2>
This project involved setting up and configuring Snort as an Intrusion Detection System (IDS) in a home lab environment. Through steps including installation, configuration, and rule customization, I successfully used Snort to monitor and analyze network traffic. By generating traffic using Nmap scans and reviewing logs in real time, I demonstrated Snort's ability to detect and log suspicious activity, showcasing proficiency in network monitoring and intrusion detection.
</p>
