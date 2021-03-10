Role Name
=========

Role Name: ctxcommunity.windows.optional_feature

This role Enables and Disables a specified Windows Optional Feature

Note: If this feature requires parent features to be enabled those features enabled
by default. Disabling this feature will only disable the feature itself but it
will not disable the parent features.

Requirements
------------

No pre-requisites.

Role Variables
--------------

The defaults/main.yml contains the following variable and default values:

  win_optional_feature_name: ~
  win_optional_feature_state: present
  win_optional_feature_include_parent: yes
  win_optional_feature_reboot: noreboot

The win_optional_feature_name MUST be defined. This is the Windows Optional Feature
to be Enabled or Disabled.  For a complete list, for a given Operating System,
run the following PowerShell command:

  Get-WindowsOptionalFeature -online | ft

The win_optional_feature_state variable controls the enablement state
for the specified Windows Optional Feature.

Possible Values are:
  present         (default) : This will Enable the specified Feature
  absent                    : This will Disable the specified Feature

The win_optional_feature_include_parent variable controls the enablement state
for parent features that are prerequisites.

Possible Values are:
  yes             (default) : This will Enable ALL parent features that are dependencies for the Feature
  no                        : This will only Enable the specified Feature. This will fail if there are
                            :   dependencies on a parent feature that are not enabled.

The win_optional_feature_reboot variable determines if the machine will be restarted after
the feature has been installed.

  noreboot        (default) : Do not reboot the machine when the Feature state is changed
  reboot                    : Reboot the machine when the Feature state is changed

It is important to note with installing multiple Windows Optional Features the previous variables
(ie win_optional_feature_reboot, win_optional_feature_include_parent, etc) will retain their values from
the prior use in the playbook and does NOT revert back to the defaults if changed.

For example:

  roles:
    - role: ctxcommunity.windows.optional_feature
      vars:
        win_optional_feature_name: msmq-http
        win_optional_feature_reboot: yes
    - role: ctxcommunity.windows.optional_feature
      vars:
        win_optional_feature_name: netfx3

After the enablement of netfx3 the system will be restarted because the default value of no for the
win_optional_feature_reboot variable has been changed to yes during the msmq-http enablement.
Reorder the enablement of the Windows Optional Features so that those features that do not need a
reboot (netfx3, for example) are enabled before those that require a reboot (msmq-http, for example).
Or simply, define the desired value as needed.

For example:   

  roles:
    - role: ctxcommunity.windows.optional_feature
      vars:
        win_optional_feature_name: msmq-http
        win_optional_feature_reboot: yes
    - role: ctxcommunity.windows.optional_feature
      vars:
        win_optional_feature_name: netfx3
        win_optional_feature_reboot: no

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
      - role: ctxcommunity.windows.optional_feature
        vars:
          win_optional_feature_name: netfx3
      - role: ctxcommunity.windows.optional_feature
        vars:
          win_optional_feature_name: msmq-http
          win_optional_feature_reboot: yes

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
