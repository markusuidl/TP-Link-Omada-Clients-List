# TP-Link-Omada-Clients-List
PHP Script to get connected devices with Omada Controller by your EAP accesspoints.
I use this script to check the state of my wifi devices and control my homeautomation.

The script is not perfect but it works. Help, wishes, improvements are welcome.

# BETA version - working (support/help wanted)

<details> 
  <summary><b>Preface: Unifi</b></summary>
   Originally I had Unifi hardware in use, there you could query the individual access points or the controller via SSH, which clients are connected.
Omada access points support SSH (after activation) but do not offer a command to query the connected clients. You always have to query via the Omada software controller.
</details>


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
10. modify the clients.php script and set the environment variables (ip, user, password)


# Problems / restrictions / To-Do:
- <b>only the first 100</b> clients are returned (tested with GetClients(1,100)
- only pagesizes from omada webinterface are working!
- having 28 clients: tested GetClients(1,10), GetClients(2,10), GetClients(3,10) where the last two returned the same results (hint for fetched all?)
- errorhandling / optimize programflow 
- automation of getting site-id
- reuse cookies until expiring
- clients disconnected for long time don't show up in list (you have to temporary fix this if your homeautomation needs the json entry, modify output, add entry with state 'off')

# Helpful
thanks to mbentley and his [shell script](https://gist.github.com/mbentley/03c198077c81d52cb029b825e9a6dc18)

 
# Thoughts
1. <b>/api/v2/sites/Default/clients/CLIENT-MAC-ADDRESS</b> thows error
2. <b>/api/v2/sites</b> does not work to get site-id
