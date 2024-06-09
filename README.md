# Sandbox Environment Setup Project

## Overview

This project involves setting up a sandbox environment with a Windows VM running FLARE VM and a REMnux VM configured with INetSim. The two VMs are connected through a host-only network, allowing them to communicate securely without internet access. This setup is useful for secure malware analysis.

## Prerequisites

- Windows 10 ISO 
- REMnux ISO
- FLARE VM installer scripts

## Steps to Set Up the Environment

### 1. Set Up the Windows VM

1. **Download the Windows 10 ISO**
   - Download link: [Windows 10 ISO](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)
     ![Windows 10 ISO Download Page](Screenshot%20(70).png)
2. **Create a new Virtual Machine in VirtualBox**
     ![VM Setup](Screenshot%20(78).png)
3. **Install Windows 10**
   - Start the newly created virtual machine and click "Install Now" to install Windows 10 in the Virtual Machine
     ![install windows10](Screenshot%20(80).png)
   - Select the "Custom" option
     ![Custom Setup](Screenshot%20(81).png)
    
   
4. **Install FLARE VM:**
   - Follow the Flare VM installation process as written in the [official repository](https://github.com/mandiant/flare-vm).
     ![Flare VM install](Screenshot%20(82).png)
