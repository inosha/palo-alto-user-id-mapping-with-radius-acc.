# palo-alto-user-id-mapping-with-radius-acc.
## HOW IT WORKS
exsiting freeradius server is listening on 1813 for raduis accounting data, once that recive data user name and IP address (ephimeral) pull out from the accouting requests and sends to the Palo Alto API.
*** 
![](images/Yellow%20Simple%20Signs%20Poster.gif)

### on OS
```
apt install python-minimal open-vm-tools git -y 
git clone https://github.com/PackeTsar/radiuid.git
cd radiuid
python radiuid.py install

```
### as a docker container
```

with SSH access : >docker run -it -p 1813:1813/udp -p 1813:1813/tcp -p 222:22/tcp --name radiuid -t packetsar/radiuid-ssh:latest

without SSH access: >docker run -it -p 1813:1813/udp -p 1813:1813/tcp --name RADIUID -t packetsar/radiuid:latest
```
*** 
```
-------------------------------------------------------------------------------------------------------------------------------
                     ARGUMENTS                    |                                  DESCRIPTIONS
-------------------------------------------------------------------------------------------------------------------------------

 - run                                            |  Run the RadiUID main program in shell mode begin pushing User-ID information
-------------------------------------------------------------------------------------------------------------------------------

 - install                                        |  Run RadiUID Install/Maintenance Utility
-------------------------------------------------------------------------------------------------------------------------------

 - show log                                       |  Show the RadiUID log file
 - show acct-logs                                 |  Show the log files currently in the FreeRADIUS accounting directory
 - show run (xml | set)                           |  Show the RadiUID configuration in XML format (default) or as set commands
 - show config (xml | set)                        |  Show the RadiUID configuration in XML format (default) or as set commands
 - show clients (file | table)                    |  Show the FreeRADIUS clients and config file
 - show status                                    |  Show the RadiUID and FreeRADIUS service statuses
 - show mappings (<target> | all | consistency)   |  Show the current IP-to-User mappings of one or all targets or check consistency
-------------------------------------------------------------------------------------------------------------------------------

 - set logfile                                    |  Set the RadiUID logfile path
 - set radiuslogpath <directory path>             |  Set the path used to find FreeRADIUS accounting log files
 - set acctlogcopypath <directory path>           |  Set the path where RadiUID should copy acct log files before deletion
 - set maxloglines <number-of-lines>              |  Set the max number of lines allowed in the log ('0' turns circular logging off)
 - set userdomain (none | <domain name>)          |  Set the domain name prepended to User-ID mappings
 - set timeout                                    |  Set the timeout (in minutes) for User-ID mappings sent to the firewall targets
 - set looptime                                   |  Set the waiting loop time (in seconds) to pause between checks of the RADIUS logs
 - set tlsversion (1.0 | 1.1 | 1.2)               |  Set the version of TLS used for XML API communication with the firewall targets
 - set radiusstopaction (clear | ignore | push)   |  Set the action taken by RadiUID when RADIUS stop messages are received
 - set client (ipv4|ipv6) <ip-block> <secret>     |  Set configuration elements for RADIUS clients to send accounting data FreeRADIUS
 - set munge <rule>.<step> [parameters]           |  Set munge (string processing rules) for User-IDs
 - set target <hostname>:<vsys-id> [parameters]   |  Set configuration elements for existing or new firewall targets
-------------------------------------------------------------------------------------------------------------------------------

 - push (<hostname>:<vsys-id> | all) [parameters] |  Manually push a User-ID mapping to one or all firewall targets
-------------------------------------------------------------------------------------------------------------------------------

 - tail log (<# of lines>)                        |  Watch the RadiUID log file in real time
-------------------------------------------------------------------------------------------------------------------------------

 - clear log                                      |  Delete the content in the log file
 - clear acct-logs                                |  Delete the log files currently in the FreeRADIUS accounting directory
 - clear client (<ip-block> | all)                |  Delete one or all RADIUS client IP blocks in FreeRADIUS config file
 - clear munge (<rule> | all) (<step> | all)      |  Delete one or all munge rules in the config file
 - clear target (<hostname>:<vsys-id> | all)      |  Delete one or all firewall targets in the config file
 - clear mappings [parameters]                    |  Remove one or all IP-to-User mappings from one or all firewalls
-------------------------------------------------------------------------------------------------------------------------------

 - edit config                                    |  Edit the RadiUID config file
 - edit clients                                   |  Edit RADIUS client config file for FreeRADIUS
-------------------------------------------------------------------------------------------------------------------------------

 - service [parameters]                           |  Control the RadiUID and FreeRADIUS system services
-------------------------------------------------------------------------------------------------------------------------------

 - request [parameters]                           |  Make system-level changes for RadiUID service
-------------------------------------------------------------------------------------------------------------------------------

 - version                                        |  Show the current version of RadiUID and FreeRADIUS
-------------------------------------------------------------------------------------------------------------------------------
```
