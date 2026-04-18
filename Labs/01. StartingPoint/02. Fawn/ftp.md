# FTP

* **File Transfer Protocol (FTP)**: a native protocol to all host operating
systems and used for a long time for simple file transfer tasks, be they automated or manual
* FTP can be easily misconfigured if not correctly understood
* FTP can be used to transfer log files from one network device to another or to a log collection server
* An employee of the client company might want to bypass file checks or firewall rules for transferring a file from themselves to their peers. Thus, security professionals must consider the many different mechanisms for controlling and monitoring data flow within an enterprise network today
* Suppose the network engineer in charge of handling the configuration forgets to secure the receiving FTP server properly or does not put enough importance on the information contained within the logs and decides to leave the FTP service unsecured intentionally. In that case, an attacker could gain leverage of the logs and extract all kinds of information from them, which can later be used to map out the network, enumerate usernames, detect active services, and more.