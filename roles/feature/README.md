Role Name
=========

Role Name: ctxcommunity.windows.feature

This role Installs and Removes a specified Windows Role/Feature

Note: If this role/feature has dependencies that are not currently installed, those
dependencies will also be installed. Removing this feature will only remove the specified
feature itself but it will not remove any dependencies previously installed.

Requirements
------------

This role should only be used on a Windows Server OS.

Role Variables
--------------

The defaults/main.yml contains the following variable and default values:

  win_feature_name: ~
  win_feature_state: present
  win_feature_reboot: noreboot
  win_feature_include_management_tools: no
  win_feature_include_sub_features: no

The win_feature_name MUST be defined. This is the Windows Feature to be
Installed or Removed.  For a complete list run the following PowerShell command
from a Windows Server:

  Get-WindowsFeature

The win_feature_state variable controls the installation state
for the specified Windows Feature.

Possible Values are:
  present         (default) : This will Enable the specified Role/Feature
  absent                    : This will Disable the specified Role/Feature

The win_feature_include_management_tools variable controls the installation state
for any related administrative management tools.

Possible Values are:
  yes                       : This will install the management tools for the specified Role/Feature
  no              (default) : This will not install the management tools for the specified Role/Feature

The win_feature_include_sub_features variable controls the installation state
for any sub features.

Possible Values are:
  yes                       : This will install the sub features for the specified Role/Feature
  no              (default) : This will not install the sub features for the specified Role/Feature


The win_optional_feature_reboot variable determines if the machine will be restarted after
the feature has been installed.

  noreboot        (default) : Do not reboot the machine when the Feature state is changed
  reboot                    : Reboot the machine when the Feature state is changed

It is important to note with installing multiple Windows Features the previous variables
(ie win_feature_reboot, win_feature_include_management_tools, etc) will retain their values from
the prior use in the playbook and does NOT revert back to the defaults if changed.

For example:

  roles:
    - role: ctxcommunity.windows.feature
      vars:
        win_feature_name: rds-server
        win_feature_reboot: yes
    - role: ctxcommunity.windows.feature
      vars:
        win_feature_name: NET-Framework-Core

After the installation of NET-Framework-Core the system will be restarted because the
default value of no for the win_feature_reboot variable has been changed to yes during
the rds-server role installation.  Reorder the enablement of the Windows Role/Features so
that those roles/features that do not need a reboot (NET-Framework-Core, for example) are
enabled before those that require a reboot (rds-server, for example).  Or simply, define
the desired value as needed.

For example:   

  roles:
    - role: ctxcommunity.windows.feature
      vars:
        win_feature_name: rds-server
        win_feature_reboot: yes
    - role: ctxcommunity.windows.feature
      vars:
        win_feature_name: NET-Framework-Core
        win_feature_reboot: no

While the defaults/main.yml file can be modified directly, future updates will
overwrite the defaults/main.yml file.  In addition, many of the roles use the same
variables and could benefit from the variable being set at a high precedence.
The variable smb_location is one such example.

To set/override the default variable values the best place(s) to accomplish this is
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
      - role: ctxcommunity.windows.feature
        vars:
          win_feature_name: NET-Framework-Core
      - role: ctxcommunity.windows.feature
        vars:
          win_feature_name: rds-server
          win_feature_reboot: yes

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
