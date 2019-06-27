Role Name
=========

polycom-vvx-voipms - Manage configurations and rebooting of Polycom VVX series VoIP phones, strongly opinionated towards voip.ms + cluetrust way of doing subaccounts

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

```yaml
- hosts: [ rs_polycoms ]
  gather_facts: no

  tasks:
    - name: generate configuration files
      include_role:
        name: polycom-vvx-voipms-config
        tasks_from: config
```

OR

```yaml
- hosts: [ rs_polycoms ]
  gather_facts: no

  tasks:
    - name: reboot phone
      include_role:
        name: polycom-vvx-voipms-config
        tasks_from: reboot
```

License
-------

MIT

Author Information
------------------

rs@cluetrust.com
https://technotes.seastrom.com

