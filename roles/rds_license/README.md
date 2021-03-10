Role Name
=========

Role Name: ctxcommunity.windows.rds_license

This role installs and removes the Windows Role RDS License Service and Administrative Tools

Requirements
------------

No pre-requisites.

Role Variables
--------------

The defaults/main.yml contains the following variable and value (as a default)

win_feature_rds_license_state: present
win_feature_rds_license_ui_state: present

The win_feature_rds_license_state: variable controls the installation state
for the Windows Role Remote Desktop License Services

Possible Values are:
  present         : This will install the RDS License Role
  absent          : This will remove the RDS License Role

The win_feature_rds_license_ui_state: variable controls the installation state
for the Windows Role Remote Desktop License Services Administrative Tools

Possible Values are:
  present         : This will install the RDS License Administrative Tools
  absent          : This will remove the RDS License Administrative Tools

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
         - ctxcommunity.windows.license

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
