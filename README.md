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

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>

<p align="center">
<img src=".jpg" height="90%", width="90%">
</p>
