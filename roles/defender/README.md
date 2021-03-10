Role Name
=========

Role Name: ctxcommunity.windows.defender

This role installs/removes the Windows Feature Windows Defender

Requirements
------------

This role should only be used on a Windows Server OS.

Role Variables
--------------

The defaults/main.yml contains the following variable and default value

  win_feature_defender_state: absent

The win_feature_defender_state variable controls the installation state
for the Windows Feature Windows Defender

Possible Values are:
  present         (default) : This will install the Windows Defender Feature
  absent                    : This will remove the Windows Defender Feature

While the defaults/main.yml file can be modified directly, future updates will
overwrite the defaults/main.yml file.  In addition, many of the roles use the same
variables and could benefit from the variable being set at a high precedence.
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
         - ctxcommunity.windows.defender

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
