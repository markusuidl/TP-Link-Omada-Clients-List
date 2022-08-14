# TP-Link-Omada-Clients-List
PHP Script to get connected devices with Omada Controller by your EAP accesspoints
I use this script to check the state of my wifi devices and control my homeautomation

# BETA version - working (support/ help wanted)

<b>Preface</b><br>
Originally I had Unifi hardware in use, there you could query the individual access points or the controller via SSH, which clients are connected.
Omada access points support SSH (after activation) but do not offer a command to query the connected clients. You always have to query via the Omada software controller.

<b>API</b>
The controller version seems to be very important, as not all endpoints always work in every version. The documentation is hard to find, I uploaded a file of another API version (might be helpful). [Link to API documentation](api_5.0.15.html)

# System-Information
- Omada Version <b>5.4.6</b> <i>(running at Debian 11 on Proxmox VM)</i>
- EAP610 accesspoints

# HOW-TO
1. login to your omada controller with Google chrome
2. (optionally) create a new user (role: viewer) and grant access to site
3. open DevTools in Chrome and open 'Network' tab
4. select 'Clients' Page on Omada Controller
5. wait in DevTools to see an entry like 'clients?currentPage=1..."
6. right click on that entry and save as HAR
7. open HAR file with editor and search for 'clients?'
8. you find an entry: ... api/v2/sites/<b>SITE-ID</b>/clients?currentPage=1 ...
9. not the SITE-ID an enter it to the [clients.php](clients.php) script
10. don't forget to modify the clients.php script
11. set '$omada_url', '$siteid', '$username', '$password'
