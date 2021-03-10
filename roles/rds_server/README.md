Role Name
=========

Role Name: ctxcommunity.windows.rds_server

This role installs and removes the Windows Role Remote Desktop Session Host

Requirements
------------

No pre-requisites.

Role Variables
--------------

The defaults/main.yml contains the following variable and value (as a default)

win_feature_rds_server_state: present

The win_feature_rds_server_state variable controls the installation state
for the Windows Role Remote Desktop Services/Remote Desktop Session Host

Possible Values are:
  present         : This will install the RDS Server Role
  absent          : This will remove the RDS Server Role

While the defaults/main.yml file can be modified directly, future updates will
overwrite the defaults/main.yml file.  In addition, many of the roles use the same
variables and would seems benefit from the variable being set at a high precedence.
The variable smb_location is one such example.

To override the default variable values the best place(s) to accomplish this is
to set the new values in one of the following locations:
  host_vars/{hostname.mycompany.com}.yml
  group_vars/{group}.yml
  group_vars/all.yml
  playbook.yml

Dependencies
------------

No dependencies.

Example Playbook
----------------

    - hosts: servers
      roles:
         - ctxcommunity.windows.rds_server

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
