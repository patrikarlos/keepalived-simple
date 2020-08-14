keepalived-simple
=================

Simple keepalived setup

Requirements
------------

At least two Servers

Role Variables
--------------

- keepalived_state (host var/inventory): "MASTER", default: "BACKUP"
- keepalived_virtual_ipaddress (group var): Virtual IP (VIP) addresses
- keepalived_chk_proc_name (undefined): Process name to check


Dependencies
------------

- None

Example Playbook
----------------

    - hosts: keepalived-servers
      roles:
         - { role: keepalived-simple }

License
-------

GPL-2.0-or-later

Author Information
------------------

Sven Velt <sven-ansiblerole@velt.biz>
https://git.velt.biz/velt.biz/

