strongswan_server
=================

Download/compile and install strongswan on server.
This role is desinged to handle android native vpn with a freeradius backend.
https://wiki.strongswan.org/projects/strongswan/wiki/XAuthEAP
```
Client <--- IKEv1/Xauth ---> Server <--- RADIUS/EAP ---> AAA
```


Requirements
------------

Tested on Debian (raspberrypi)

Role Variables
--------------

* strongswan_server_dns: external dns name
* strongswan_server_git_directory: strongswan git compilation directory
* strongswan_server_radius_address: radius server ip
* strongswan_server_radius_secret: radius server secret
* strongswan_server_radius_auth_port: radius auth_port
* strongswan_server_radius_acct_port: radius acct_port 

Dependencies
------------

N/A

Example Playbook
----------------


    - hosts: servers
      roles:
         - { role: strongswan_server, strongswan_server_dns: "hello.world.lab" }

License
-------

BSD

