Role Name
=========

polycom-vvx-voipms-config - Makes config files for Polycom VVX phones, strongly opinionated towards voip.ms + cluetrust way of doing subaccounts

Requirements
------------

None

Role Variables
--------------

These should be set in groups_vars/all.yml or group_vars/your_group.yml - you might even want to override in host_vars/00005e00532a.yml

voipms_account: "123456"
voipms_server: "washington1.voip.ms"

Credentials for the phone to talk to the provisioning server

provisioning_server: polyanna.example.org
provisioning_server_scheme: https
provisioning_server_username: PlcmSpIp
provisioning_server_password: some_password

Note that the hostname in the inventory file is the MAC address of the phone.  The operation is delegate_to the provisioning server

phone_password: 31337 (this is the login or front panel login pin/password for the phone)

These variables you likely want to set in host_vars/00005e00532a.yml

sippassword: "some_password" (this is the password for sip registration, assumption is that you make it the same for all buttons on a phone)

clock24: 1

buttons array - minimum is just a series of labels - the defaults on
the back end will do the needful.  something like this, up to the
maximum number of buttons your phone supports:

buttons:

  - displayname: "7036212332"

  - label: "Spoof Cell (0001)"
    displayname: "7036220001"


Each button on the phone is a separate SIP registration to voip.ms.
They do subaccounts by concatenating account name + underscore +
user-defined-subaccount-name (with serious restrictions on characters).

For ClueTrust, the approved user-defined subaccount name is the last 6
digits of the MAC address (no colons) plus a two digit button number
starting at 01 (Polycom's button number index starts at 1 not 0).

So, button 1 for voip.ms account 123456 Polycom phone MAC address 00:00:5e:00:53:2a would be 123456_00532a01

This role handles all that on the back end in the phone config definitions.

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

