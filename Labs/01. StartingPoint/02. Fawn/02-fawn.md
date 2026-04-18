# Fawn

## FTP

* **File Transfer Protocol (FTP)**: a native communication protocol to all host operating systems and used for a long time for simple file transfer tasks, be they automated or manual. Used to transfer files from a server to client on a computer network.
  
<p align="center">
  <img src="https://github.com/thespcrewroy/HackTheBox/blob/main/assets/client-server-architecture.png" alt="Client Server Architecture" />
</p>

> Client–server model architecture with separate control (port 21) and data (port 20) connections between the client and the server

* Can be easily misconfigured if not correctly understood
* Can be used to transfer log files from one network device to another or to a log collection server
* An employee of the client company might want to bypass file checks or firewall rules for transferring a file from themselves to their peers. Thus, security professionals must consider the many different mechanisms for controlling and monitoring data flow within an enterprise network today
* Suppose the network engineer in charge of handling the configuration forgets to secure the receiving FTP server properly or does not put enough importance on the information contained within the logs and decides to leave the FTP service unsecured intentionally. In that case, an attacker could gain leverage of the logs and extract all kinds of information from them, which can later be used to map out the network, enumerate usernames, detect active services, and more.
* Clients can also browse the available files on the server using common linux commands like `ls` or `cd`
* FTP come with a GUI (Graphical User Interface) making them beginner friendly

## Open Ports
* A port running an active service is a reserved space for the IP address of the target server to receive requests and send results from
* Ports are necessary because if we only had IP addresses or hostnames, then the hosts could only perform one service per IP address
* By having ports, you can have one IP address handling multiple services simeoultaneously
* Thus, the purpose of ports is to add a layer of distinction

<p align="center">
  <img src="https://github.com/thespcrewroy/HackTheBox/blob/main/assets/simple-webserver.png" alt="Simple Webserver" />
</p>

* A rudimentary core web server configuration sets up FTP, SSH, and HTTP can:
    * Receive and send files that can be used to configure the webserver
    * Receive and send server logs to an external source
    * Log in for remote management from a distant host
    * Serve web content that can be accessed remotely through another host's browser

## Securing FTP
* Users may authenticate themselves with a clear-text sign-in protocol such as username and password
* Users can connect anonymously with username `anonymous` without having a password if the server is configured for it

<p align="center">
  <img src="https://github.com/thespcrewroy/HackTheBox/blob/main/assets/mitm.png" alt="Simple Webserver" />
</p>

* For secure encrypted transmission, FTP is often secured with SSL/TLS (FTPS) or SSH (SFTP)
* FTP does not encrypt the traffic sent between client and server
* Traffic can be intercepted with what is known as a Man-in-the-Middle Attack (MitM), and the contents of the files can be read

<p align="center">
  <img src="https://github.com/thespcrewroy/HackTheBox/blob/main/assets/sftp.png" alt="Simple Webserver" />
</p>


* Network administrators can wrap the connection with the SSL/TLS protocol or tunnel the FTP connection through SSH to add a layer of encryption that only the source and destination hosts can decrypt to foil most Man-in-the-Middle attacks
* Port 21 has disappeared, as the FTP protocol gets moved under the SSH protocol on port 22, thus being tunneled through it and secured against any interception.