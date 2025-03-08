# Incident-Monitoring-and-Detection-with-EDR

 ## Objective
 
The primary objective of the Monitoring and Detection project was to employ EDR solutions such as LimaCharlie - a cross-platform EDR agent, to effectively monitor and detect security threats including credential dumping attacks and C2 payloads. The purpose of this practical experience was to equip me with the neccessary practical skills and knowldge to effectively monitor credential dumping attacks, understand how to use Sysmon to get concrete granular telemetry on my windows endpoint activities.  

### Skills Learned


- Proficiency in deploying and configuring Virtual machines, including Linux and Windows Operating Systems
- Proficiency in troubleshooting and configuring Windows defender & firewall rules
- Proficiency in identifying and monitoring C2 payloads and credential dumping attacks
- Enhanced understanding of EDR telemetry and event logs for endpoint devices
- Proficiency in generating, executing and analyzing C2 payloads 
- Proficiency in threat detection and response & tuning false positives
- Proficiency in crafting detection and response (D&R) rules & crafting rules to block attacks

  ### Tools Used

  - LimaCharlie (EDR tool) for effective monitoring, detection and response of malicious processes  
  - Sysmon for getting granular telemetry on my endpoint devices
  - Sliver server to generate C2 payloads for malicious activity
  - YARA tool for identifying, classifying malware and crafting rules to block attacks
  - Virtual machines (VMWare Workstation pro, Ubuntu Linux, Windows 10)
 
## Steps

#### Downloaded, unzipped, installed and validated Sysmon here: 

 <img width="860" alt="Sysmon" src="https://github.com/CyberHaack/Incident-Monitoring-and-Detection-with-EDR/assets/163551482/5d7b93f6-4dff-416d-8e8f-ae9dc4839216">



#### Installed LimaCharlie Agent (EDR tool) for monitoring and detecting the C2 payloads I'd be generating and infecting my client VM with.

 <img width="860" alt="2" src="https://github.com/CyberHaack/Incident-Monitoring-and-Detection-with-EDR/assets/163551482/61015bdd-31c2-4293-9965-fb54619ceb7b">


#### Downloaded Sliver Server, a Command and Control (C2) framework on my attack machine (Ubuntu)  which will be used to generate malicious implants

<img width="860" alt="3" src="https://github.com/CyberHaack/Incident-Monitoring-and-Detection-with-EDR/assets/163551482/2c4637e4-44b3-4504-9d0d-e37cee175b42">

#### Generated a C2 payload here, called "PASSING_SLAPSTICK.exe"


<img width="860" alt="4" src="https://github.com/CyberHaack/Incident-Monitoring-and-Detection-with-EDR/assets/163551482/1560d2c6-bea9-4a8c-8938-06d36d67cf93">

<img width="860" alt="5" src="https://github.com/CyberHaack/Incident-Monitoring-and-Detection-with-EDR/assets/163551482/bf8d3ac6-00ca-417a-95a5-bce91d001ef6">


#### Injected the malicious implants from my attack machine (Ubuntu) to my client machine (Windows VM) using python3 to spin up a temporary web server


<img width="860" alt="6" src="https://github.com/CyberHaack/Incident-Monitoring-and-Detection-with-EDR/assets/163551482/fbf04db4-0b78-4e7e-bb6b-fb6e6c31c966">


#### Started the Command and Control Session on my attack machine, executed and interacted with the C2 payload using Administrative powershell prompt on the client VM. 

<img width="860" alt="7" src="https://github.com/CyberHaack/Incident-Monitoring-and-Detection-with-EDR/assets/163551482/d12a4789-e8e5-42b0-ad35-13f03b256a0e">

### I want you to take note of the highlighted part on the screenshot below which shows just how high the privilege we have is (SeDebugPrivilege and SeImpersonatePrivilege), this allows us to carry out further attack on the machine
<img width="927" alt="7b" src="https://github.com/user-attachments/assets/ecbf038c-dc33-4a5c-84ed-3c182b9c2153" />

### Let's move over to LimaCharlie to observe the telemetry from the Web UI: 

##### Click on Sensors by the left pane, then select the active windows section
#### Click on Processes. This will display a list of all running processes, both active and inactive. I recommend taking some time to review these processes to understand their normal behavior, as this will make it easier to identify any abnormalities. Without knowing what is normal, it will be difficult to recognize what is abnormal.

#### By hovering your cursur over the Yellow and Grey Wifi icon, I could see that the processes with a yellow wifi icon indicates that the process is listening and active on the network, while the grey wifi indicates that the process is only listening on the network. 

<img width="898" alt="8" src="https://github.com/user-attachments/assets/518818a5-a18a-4c73-8a4b-8e7665afc84e" />

#### We should see that our C2 Implant "PASSING_SLAPSTICK.exe" is showing as an unsigned process. This is one of the ways to filter illegitimate processes running on your Machine.

##### Note: The processes marked with a green check are typically legitimate. However, some malware can exploit these legitimate processes to carry out attacks.

#### Investigating further, we can also see the destination IP address this process is coming from by going to Network

<img width="953" alt="9" src="https://github.com/user-attachments/assets/33a37a6b-2368-4164-9e78-f3708ec9ee7d" />

<img width="865" alt="{C0B23606-25D8-4FBA-80D3-041EA183AEE1}" src="https://github.com/user-attachments/assets/42abe671-16ce-461b-96ce-436ef5881566" />


#### Explore the Network section to gather detailed information that will support your analysis. 

#### Here, I explored the File System section and browsed to the location where my implant is running from by clicking on File System 
<img width="960" alt="10" src="https://github.com/user-attachments/assets/627e8085-61bf-4ce7-b9ff-ea5f8d1511b5" />

#### I inspected the hash of the executable file by running it through VirusTotal. Interestingly, no detections were found. Here’s how VirusTotal works: when you scan a file, hash, or URL, it checks against a database of known malware signatures. If the scanned item does not match any known signatures, VirusTotal may not return any results. However, this does not necessarily mean the file is safe. Therefore, I strongly recommend using a more advanced tool for further analysis. 


### In Progress............
