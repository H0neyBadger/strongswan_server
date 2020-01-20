strongswan_server
=================

Download/compile and install strongswan on server.
This role is desinged to handle android native vpn with a freeradius backend.
https://wiki.strongswan.org/projects/strongswan/wiki/XAuthEAP
```
Client <--- IKEv1/Xauth ---> Server <--- RADIUS/EAP ---> AAA
```

### iptables 
iptables/firewall nat rules are not in the scope of this role. 
```
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -m policy --dir out --pol ipsec -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
```

### radius
radius install/config is not in the scope of this role
```
apt-get install freeradius
```



Requirements
------------

Tested on Debian (raspberrypi)

Role Variables
--------------

* strongswan_server_leftid: external ipsec server name or ip
* strongswan_server_leftdns: (optional) internal 'left' network dns sever
* strongswan_server_git_directory: (optional) strongswan git compilation directory
* strongswan_server_radius_address: (optional) radius server ip
* strongswan_server_radius_secret: (optional) radius server secret
* strongswan_server_radius_auth_port: (optional) radius auth_port
* strongswan_server_radius_acct_port: (optional) radius acct_port 

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

