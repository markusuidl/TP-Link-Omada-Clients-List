# TP-Link-Omada-Clients-List
PHP Script to get connected devices with Omada Controller by your EAP accesspoints

# BETA version - working (support/ help wanted)

<b>Preface</b><br>
Originally I had Unifi hardware in use, there you could query the individual access points or the controller via SSH, which clients are connected.
Omada access points support SSH (after activation) but do not offer a command to query the connected clients. You always have to query via the Omada software controller.

<b>API</b>
The controller version seems to be very important, as not all endpoints always work in every version. The documentation is hard to find, I uploaded a file of another API version (might be helpful).

# System-Information
- Omada Version 5.4.6 
- running at Debian 11 on Proxmox VM
- using four EAP610 accesspoints


I use this script to check the state of my wifi devices and control my homeautomation
