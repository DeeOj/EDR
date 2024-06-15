# PROJECT: ENDPOINT DETECTION AND RESPONSE (HOMELAB)

## INTRODUCTION

This lab involves setting up two virtual machines: one as an attack machine running Ubuntu Server and another as a victim machine running Windows 11. The attack machine is used to execute adversarial commands, mimicking the actions of a threat actor. The victim machine is equipped with Sysmon for detailed system monitoring and LimaCharlie EDR for advanced threat detection and response capabilities. Through this setup, utilizing Eric Capuano's guide, I explore the processes of telemetry collection, detection rule creation, and response rule implementation to effectively neutralize simulated attacks.

## OBJECTIVE
The primary objective of this project is to simulate a realistic cyber attack scenario and demonstrate effective detection and response strategies using advanced security tools

## LINKS TO RESOURCES
- [Ubuntu server 22.04.1](https://releases.ubuntu.com/22.04.1/ubuntu-22.04.1-live-server-amd64.iso)
- [Window 11 ISO](https://www.microsoft.com/software-download/windows11)
- [LimaCharlie](https://app.limacharlie.io/orgs)
- [Eric's guide](https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro?sd=pf)



## UBUNTU SERVER SETUP

- Hardware configurations
<p align="center">
<img src="https://imgur.com/hSlGJ4x.jpg" height="90%", width="90%">
</p>

- Boot up
<p align="center">
<img src="https://imgur.com/I3eWxYs.jpg" height="90%", width="90%">
</p>

- Here, I will set the IP address for the VM to be static
<p align="center">
<img src="https://imgur.com/U2bCESv.jpg" height="90%", width="90%">
</p>

- Copied the the subnet and gateway IPs
<p align="center">
<img src="https://imgur.com/lvLeYpR.jpg" height="90%", width="90%">
</p>

- Set VM with it
<p align="center">
<img src="https://imgur.com/sMpDXua.jpg" height="90%", width="90%">
</p>


- Set Credentials
<p align="center">
<img src="https://imgur.com/WqzcVj7.jpg" height="90%", width="90%">
</p>

- Installed OpenSSH server
<p align="center">
<img src="https://imgur.com/0p56snE.jpg" height="90%", width="90%">
</p>

- Logged in
<p align="center">
<img src="https://imgur.com/pidwKB0.jpg" height="90%", width="90%">
</p>

- Testing connectivity
<p align="center">
<img src="https://imgur.com/nJwRlpq.jpg" height="90%", width="90%">
</p>

## DISABLING DEFENDER ON WINDOWS VM

- Turn off tamper alongside other protections.
<p align="center">
<img src="https://imgur.com/qOdNJU6.jpg" height="90%", width="90%">
</p>

- Permanently disable Defender via Group Policy Editor

<p align="center">
<img src="https://imgur.com/voHSO49.jpg" height="90%", width="90%">
</p>

- Permanently disable Defender via registry

<p align="center">
<img src="https://imgur.com/4zNNOCY.jpg" height="90%", width="90%">
</p>

- Boot into safe mode and disable all denfender services

<p align="center">
<img src="https://imgur.com/g9pWova.jpg" height="90%", width="90%">
</p>

- In the registry editor, change the "start" value to 4, for the following and boot out of safe mode afterwards;

1. Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Sense

2. Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WdBoot

3. Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WinDefend

4. Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WdNisDrv

5. Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WdNisSvc

6. Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WdFilter

- Preventing VM from going into standby.

<p align="center">
<img src="https://imgur.com/gMs52Ov.jpg" height="90%", width="90%">
</p>

## INSTALLING SYSMON IN WINDOWS VM
<p align="center">
<img src="https://imgur.com/aPhCXc4.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/Ck6PJ1q.jpg" height="90%", width="90%">
</p>

- Checking for Sysmon Event Logs
<p align="center">
<img src="https://imgur.com/t5020v7.jpg" height="90%", width="90%">
</p>

## INSTALL LIMACHARLIE EDR ON WINDOWS VM

- Create an account and also an Organization
<p align="center">
<img src="https://imgur.com/yDYvzak.jpg" height="90%", width="90%">
</p>

- Install sensors on VM
<p align="center">
<img src="https://imgur.com/nvdWDhZ.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/VjR7imX.jpg" height="90%", width="90%">
</p>

- Windows machine detected
<p align="center">
<img src="https://imgur.com/R18le71.jpg" height="90%", width="90%">
</p>

- Configure LimaCharlie to ship sysmon event logs alongside its own EDR telemetry
<p align="center">
<img src="https://imgur.com/RPktJFM.jpg" height="90%", width="90%">
</p>

## SETUP ATTACK SYSTEM(SLIVER)

- ssh from my host computer to Linux VM.
  
<p align="center">
<img src="https://imgur.com/LA01mYi.jpg" height="90%", width="90%">
</p>

- Dowloaded Sliver
  
<p align="center">
<img src="https://imgur.com/Pqaq176.jpg" height="90%", width="90%">
</p>


<p align="center">
<img src="https://imgur.com/Q5HBRM5.jpg" height="90%", width="90%">
</p>

- Generated C2 payload and spinned up a web server
  
<p align="center">
<img src="https://imgur.com/EKzqEzA.jpg" height="90%", width="90%">
</p>

- Downloaded into the Windoms VM

<p align="center">
<img src="https://imgur.com/pltBxGF.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/KXC5ar3.jpg" height="90%", width="90%">
</p>

- Executed the payload
<p align="center">
<img src="https://imgur.com/7Q42Pi4.jpg" height="90%", width="90%">
</p>

- Interacting with the C2 session
  
<p align="center">
<img src="https://imgur.com/qDWfpYc.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/LR5oBmz.jpg" height="90%", width="90%">
</p>

- Observing Telemetry
  
<p align="center">
<img src="https://imgur.com/GnGkFz0.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/9b2Rtwu.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/qYxHcr4.jpg" height="90%", width="90%">
</p>

## ADVERSARIAL ACTIONS
LSASS is responsible for enforcing the security policy on the system, handling password changes, and creating access tokens. It stores various types of authentication data, including plaintext passwords, hashed passwords, making it attractive to attackers. So, I will be dumping lsass, simulating a possible attack.

- Through Sliver
<p align="center">
<img src="https://imgur.com/NlkWHOc.jpg" height="90%", width="90%">
</p>

- Picked it up on the Timeline
  
<p align="center">
<img src="https://imgur.com/Jjc7mjE.jpg" height="90%", width="90%">
</p>

- No detections yet on LimaCharlie for the activity I performed against the windows VM

<p align="center">
<img src="https://imgur.com/rXzc8xv.jpg" height="90%", width="90%">
</p>

- Wrote A detection rule and a "report" response.

<p align="center">
<img src="https://imgur.com/B6tr7eN.jpg" height="90%", width="90%">
</p>

- Tested the detection rule
  
<p align="center">
<img src="https://imgur.com/iP6jLAO.jpg" height="90%", width="90%">
</p>

- Saved the rule
  
<p align="center">
<img src="https://imgur.com/zs0XJnu.jpg" height="90%", width="90%">
</p>

- Performed the same dumping of lsass on sliver, and now it shows in "Detections"
  
<p align="center">
<img src="https://imgur.com/25wyiMA.jpg" height="90%", width="90%">
</p>

## PERFORMING ANOTHER ATTACK AND BLOCKING THE ATTACK
For this I will simulate a ransomware attack and craft a response rule that effectively disrupts and blocks the attack. <br/>
As an adversary, I will be deleting volume shadows from the victim system (windows vm), since this is a predictable action of ransomware, a high threat activity and low false positive prevalence.

- C2 session
<p align="center">
<img src="https://imgur.com/LVIQTBw.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/Fqr1pbA.jpg" height="90%", width="90%">
</p>

- On LimaCharlie's Timeline
<p align="center">
<img src="https://imgur.com/DGZ6l6h.jpg" height="90%", width="90%">
</p>

- Customed response
<p align="center">
<img src="https://imgur.com/QDt4HwQ.jpg" height="90%", width="90%">
</p>

- Reran "vssadmin delete shadows /all", however we see an inactive system shell, signifying parent process has been terninated.
<p align="center">
<img src="https://imgur.com/aOG6VM9.jpg" height="90%", width="90%">
</p>

- Response rule also Seen in "Detections"
<p align="center">
<img src="https://imgur.com/kPX11ej.jpg" height="90%", width="90%">
</p>
