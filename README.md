<h1>Port Scanning - Network Penetration testing</h1>
Port scanning is a network reconnaissance method used to detect open ports and running services, helping security teams assess exposure and identify potential misconfigurations.

## Disclaimer
This project was conducted strictly in a controlled lab environment for educational purposes only.

## Lab Environment
- Attacker Machine: Kali Linux
- Target Machine: Metasploitable2
- Tool: Nmap
- Network Type: Isolated / Host-only Network
  
## Analysis flow
<b>1. Lab Environment</b>
<br>
This image shows a controlled cybersecurity lab using two virtual machines. On the left is Metasploitable 2, an intentionally vulnerable system used for security testing. On the right is Kali Linux, a penetration testing platform used to perform port scanning and network analysis. Both machines are isolated in a virtual network to safely simulate real-world security assessment scenarios.

<b>2. VM IP Address</b><br>
This image shows IP address identification in a controlled cybersecurity lab. On the left, Kali Linux uses the ip a command to determine the attacker machine’s network address. On the right, Metasploitable 2 uses ifconfig to display its assigned IP. Identifying target IP addresses is a critical prerequisite before performing port scanning and network security assessment in an isolated environment.

<b>3.Scanning open service and version</b><br>
The scan confirms that the host is online and reveals various services related to remote access, web applications, file sharing, and databases.this result demonstrates how service discovery helps provide visibility into system configurations and highlights the importance of monitoring exposed services within a network environment.

<b>4. Operating System Scan</b><br>
This scan identifies open services and estimates the operating system of the victim

<b>5. Vulnerability Assesment</b><br>
This image shows the result of an Nmap vulnerability scan identifying a critical backdoor in VSFTPD version 2.3.4 on FTP port 21. The service was confirmed as exploitable, demonstrating successful detection of a known remote command execution vulnerability.


## Findings
Based on the Nmap scanning results, multiple open ports and services were identified on the target machine, including FTP (21), SSH (22), HTTP (80), SMB (139/445), MySQL (3306), PostgreSQL (5432), and several legacy services such as Telnet and RPC. Service and version detection revealed outdated software running on the system, notably VSFTPD version 2.3.4 on port 21. The scan also successfully identified the operating system as Linux kernel 2.6.x, indicating the host is running an old and potentially unsupported OS. These findings demonstrate how port scanning can expose the attack surface of a system by revealing active services, software versions, and underlying operating system details.

Further analysis confirmed that VSFTPD 2.3.4 contains a known backdoor vulnerability that allows remote command execution. This shows that exposed and unpatched services significantly increase the risk of system compromise. With many unnecessary ports open and vulnerable services running, an attacker could leverage one compromised service to gain initial access and potentially perform further exploitation or lateral movement within the network.

## Mitigation
To mitigate these risks, systems should minimize their exposed attack surface by closing unused ports and disabling unnecessary services. All running services must be kept up to date with the latest security patches, especially critical services such as FTP, web servers, and database services. Insecure protocols like FTP and Telnet should be replaced with encrypted alternatives such as SFTP and SSH. Additionally, implementing firewall rules, network segmentation, and regular vulnerability scanning can help detect and prevent exploitation early. Keeping the operating system updated and supported is also essential to reduce exposure to known vulnerabilities.
