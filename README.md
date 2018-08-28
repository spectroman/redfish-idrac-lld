# iDRAC RedFish monitoring framework

With this you can use the feature from iDRAC called redfish, which is a RESTful API.

He will auto discover most of the important hardware components and add them to your monitoring.

Built in Ruby

### Instructions

#### On Zabbix side

  - Copy the files redfish-* to your "externalscripts" directory on Server or Proxy
  - Create a directory called "redfish" inside the external scripts, and make sure it is zabbix writable (`chown zabbix. redfish` at least, or give some more `chmod` rights)
  - Import the template (v4 or v3.4)
  - You must add 3 macros on the server or on the template, by default now are:
    * {$PASSWORD} with the password for iDRAC
    * {$USER} with the username to be used
    * {$IPMI} the reachable address from iDRAC
  - Make sure your iDRAC is reachable from the zabbix server/proxy, test with: `telnet 12.23.34.54 443`
  - You should edit the `redfish-collect` and `redfish-lld` and make sure the variable LOCALPATH is pointing to the location of the `redfish` directory created above

  
#### On the iDRAC side

  - Add a user on your iDRAC that contains only the rights to Login and Debug, he will be auto select type as "Operator", also give it a password.
