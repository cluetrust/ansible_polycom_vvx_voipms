Role Name
=========

polycom-vvx-voipms-config - Makes config files for Polycom VVX phones, strongly opinionated towards voip.ms + cluetrust way of doing subaccounts

Requirements
------------

None

Role Variables
--------------

See defaults/main.yml ya heathen

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: polycoms
      gather_facts: no
      roles:
         - polycom-vvx-voipms-config

License
-------

MIT

Author Information
------------------

rs@cluetrust.com
https://technotes.seastrom.com

