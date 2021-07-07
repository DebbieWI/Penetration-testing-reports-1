## Step 1: Google Dorking

●	Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is:
The Chief executive Officer of the Altoro Mutual organization is Karl Fitzgerald. Using the command, info:demotestfire.net on google, the information was retrieved.
 
![image](https://user-images.githubusercontent.com/72705930/124701193-24f22900-debc-11eb-8836-28c29bc2618f.png)
![image](https://user-images.githubusercontent.com/72705930/124701213-2b80a080-debc-11eb-9c1e-8584280669e9.png)



●	How can this information be helpful to an attacker:
The Information can enable an attacker to carry out different attacks such as Social Engineering.

## Step 2: DNS and Domain Discovery
Enter the IP address for demo.testfire.net into Domain Dossier and answer the following questions based on the results:
1.	Where is the company located:  Sunnyvale CA
2.	What is the NetRange IP address: 65.61.137.64 - 65.61.137.127

3.	What is the company they use to store their infrastructure: Rackspace Backbone Engineering

4.	What is the IP address of the DNS server: 65.61.137.117

 ![image](https://user-images.githubusercontent.com/72705930/124701242-39362600-debc-11eb-9ce2-da77f2c62b42.png) ![image](https://user-images.githubusercontent.com/72705930/124701259-418e6100-debc-11eb-8c6a-f31a87291891.png)
 
![image](https://user-images.githubusercontent.com/72705930/124701277-494e0580-debc-11eb-9227-1d3d0539e94f.png)



## Step 3: Shodan
●	What open ports and running services did Shodan find:  Ports 80 and 443
* The command shodan.io 65.61.137.117

 ![image](https://user-images.githubusercontent.com/72705930/124701335-61be2000-debc-11eb-9f22-30008ac7ab08.png)
            

## Step 4: Recon-ng

  -	Install the Recon module xssed.
  -	Set the source to demo.testfire.net.
  -	Run the module.
  - Command modules search to confirm if the module xssed is already installed
  - Command marketplace install xssed to install the recon module xssed
  - Run options set SOURCE demo.testfire.net to set the source as as demo.testfire.net
  - Command modules load recon/domains-vulnerabilities/xssed this will change the directory
  - Command info will display result of change
  - Command exploit or run will run the module
 
![image](https://user-images.githubusercontent.com/72705930/124701433-916d2800-debc-11eb-8252-98b3b58bc030.png)
![image](https://user-images.githubusercontent.com/72705930/124701458-9a5df980-debc-11eb-9066-541c17e7fe54.png)

 

The result of the output is stored in a file following the below steps 
 - Modules load reporting/html 
 - Set creator to attacker and customer as Darkweb
 - Use the command run to save the output in a file
 - To read the file use the syntax xdg-open /root/.recon-ng/workspaces/default/results.html

 ![image](https://user-images.githubusercontent.com/72705930/124701469-a5b12500-debc-11eb-8e1f-a552a438838c.png)


Is Altoro Mutual vulnerable to XSS: Yes. The output shows it has one vulnerability

## Step 5: Zenmap
Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:
●	Command for Zenmap to run a service scan against the Metasploitable machine:
Nmap -sV 192.168.0.10

●	Bonus command to output results into a new text file named zenmapscan.txt:
Nmap -sV -oN zenmap.txt 192.168.0.10

●	Use Zenmap's scripting engine to identify a vulnerability associated with the service running on the 139/445 port from your previous scan. 
The service running on both ports is Samba smbd 3.X version, and in order to identify the vulnerability associated to both ports using the Zenmap scripting engine; in the usr/share/nmap/scripts/ directory use the command 					 nmap --script - smb-enum-shares.nse 192.168.0.10

 ![image](https://user-images.githubusercontent.com/72705930/124701525-beb9d600-debc-11eb-9f78-cdb658839d25.png)



●	Once you have identified this vulnerability, answer the following questions for your client:

1.	What is the vulnerability: 
   * anonymous users has read and write access to the sumba shares

2.	Why is it dangerous: 
   * they can access company’s files and make changes to them.

3.	What mitigation strategies can you recommend for the client to protect their server:
   * disable anonymous access, and patch the server. 

