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

### In Progress............
