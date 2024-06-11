# Sandbox Environment Setup Project

## Overview

This project involves setting up a sandbox environment with a Windows VM running FLARE VM and a REMnux VM configured with INetSim. The two VMs are connected through a host-only network, allowing them to communicate securely without internet access. This setup is useful for secure malware analysis.

## Prerequisites

- Windows 10 ISO 
- REMnux ISO
- FLARE VM installer scripts

## Steps to Set Up the Environment

### 1. **Download the Windows 10 ISO**
   - Download link: [Windows 10 ISO](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)
     ![Windows 10 ISO Download Page](Screenshots/Screenshot%20(70).png)

### 2. **Create a new Virtual Machine in VirtualBox**
   - Virtual box setup:
     ![VM Setup](Screenshots/Screenshot%20(78).png)

### 3. **Install Windows 10**
   - Start the newly created virtual machine and click "Install Now" to install Windows 10 in the Virtual Machine
     ![install windows10](Screenshots/Screenshot%20(80).png)
   - Select the "Custom" option
     ![Custom Setup](Screenshots/Screenshot%20(81).png)
    
   
### 4. **Install FLARE VM:**
   - When the Windows 10 installation is finished, disable the automatic proxy setup
     ![proxy setup](Screenshots/Screenshot%20(92).png)
   - Turn off all Windows Defender settings
     ![Windows Defender Settings](Screenshots/Screenshot%20(93).png)
   - Turn off Windows Defender Antivirus from GPO
     ![Windows Defender Antivirus](Screenshots/Screenshot%20(94).png)
   - Disable Windows Firewall for both Domain Profile and Standard Profile
     ![Domain Profile](Screenshots/Screenshot%20(95).png)
     ![Standard Profile](Screenshots/Screenshot%20(96).png)
   - Follow the Flare VM installation process written in the [official repository](https://github.com/mandiant/flare-vm).
     ![Flare VM install](Screenshots/Screenshot%20(82).png)
   - Wait for installation to finish.
   - **Installation can take a very long time to finish**
     ![flare VM](Screenshots/Screenshot%20(98).png)

### 5. **Install REMnux:**
   - Download REMnux OVA file: [REMnux OVA](https://app.box.com/s/8matvs5l0gc8vkr4xfq3szdm7mc9o0ad)
   - Create a new Virtual Machine using the OVA file.
     ![REMnux VM](Screenshots/Screenshot%20(103).png)

### 6. Create a Host-Only Network.
   - On VirtualBox configure a new Host-Only Network. Configure both Adaptar and DHCP server.
     ![Host-only Network Adaptar](Screenshots/Screenshot%20(99).png)
     ![Host-only Network DHCP](Screenshots/Screenshot%20(100).png)
   - Add the newly created Host-Only Network to both VMs
     ![Windows VM](Screenshots/Screenshot%20(101).png)
   - Check IP addresses for both VMs
     ![Windows IP](Screenshots/Screenshot%20(102).png)
     ![REMnux IP](Screenshots/Screenshot%20(104).png)

### 7. **Configure INetSim on REMnux**
   - REMnux comes with INetSim Installed. To change its configuration open its configuration file.
     ```bash
        sudo scite /etc/inetsim/inetsim.conf
     ```
   - Uncomment "start service dns"
   - Change "service bind address" to 0.0.0.0
     ![inetsim.conf](Screenshots/Screenshot%20(105).png)
   - Change "dns_default_ip" to REMnux's IP address
     ![inetsim.conf default ip](Screenshots/Screenshot%20(111).png)
   - Save the file and then start INetSim
     ```bash
     inetsim
     ```
     ![inetsim](Screenshots/Screenshot%20(108).png)
   - On Windows VM open a browser and connect to REMnux's IP address, it will open the INetSim's default webpage
     ![inetsim webpage](Screenshots/Screenshot%20(109).png)
   - On the Windows VM, change the DNS Server address to REMnux's IP address
     ![Windows VM DNS](Screenshots/Screenshot%20(110).png)
   - On the browser, type any random web address, it will open the INetSim's default webpage
     ![inetsim webpage](Screenshots/Screenshot%20(112).png)
   - To test connectivity in both VMs, ping RMEnux from Windows VM and vice-versa
     ![ping](Screenshots/Screenshot%20(113).png)

## Conclusion
   We now have a sandbox environment with a Windows VM running FLARE VM and a REMnux VM running INetSim, connected through a host-only network. This setup provides a           secure environment for analyzing malware and simulating network traffic without risking your primary network.
