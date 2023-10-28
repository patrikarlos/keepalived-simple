keepalived-simple
=================

Simple keepalived setup

Requirements
------------

At least two Servers

Role Variables
--------------

Required:
- keepalived_state (host var/inventory): "MASTER", default: "BACKUP".
- keepalived_virtual_ipaddress (group var): Virtual IP (VIP) addresses. Should be a single string. 
- keepalived_router_id: RouterID, should be uniqe per cluster, if you have multipe keepalived's running.

Recommended:
- keepalived_interface: Device to listen on, defaults to eth0.

Optional:
- keepalived_chk_proc_name (undefined): Process name to check (optional)


Dependencies
------------

- None

Example Playbook
----------------
(inventory:
...
keepers:
  hosts:
    n1:
      keepalived_state: MASTER
      keepalived_prio: 255
    n2:
      keepalived_state: BACKUP
      keepalived_prio: 250
    n3:
      keepalived_state: BACKUP
      keepalived_prio: 245
      keepalived_interface: eno1
....
)

    - hosts: keepalived-servers
      roles:
         - { role: keepalived-simple }

- name: Keepalived
  hosts: keepers
  vars:
    keepalived_virtual_ipaddress: "192.168.32.47"
    keepalived_router_id: 43
    keepalived_interface: eno0
  roles:
    - keepalived-simple


License
-------

GPL-2.0-or-later

Author Information
------------------

2021-12-08, 26a0602022567d2b3933be6a0b73a4915c9f73cf, Sven Velt <sven-ansiblerole@velt.biz>, https://git.velt.biz/velt.biz/

