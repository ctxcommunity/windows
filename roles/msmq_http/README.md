Role Name
=========

Role Name: ctxcommunity.windows.msmq_http

This role Enables and Disables the Windows Optional Feature MSMQ HTTP

Note: This feature requires parent features to be enabled and will enable
those requires by default. Disabling this feature will only disable the feature
itself but it will not disable the parent features.

Requirements
------------

No pre-requisites.

Role Variables
--------------

The defaults/main.yml contains the following variable and default value:

  win_feature_msmq_http_state: present

The win_feature_msmq_http_state variable controls the enablement state
for the Windows Optional Feature for NET 3 Framework

Possible Values are:
  present         (default) : This will Enable the MSMQ HTTP Feature
  absent                    : This will Disable the MSMQ HTTP Feature

The win_feature_msmq_http_include_parent variable controls the enablement state
for parent features that are prerequisites.

Possible Values are:
  yes             (default) : This will Enable ALL parent features that are dependencies for the MSMQ HTTP Feature
  no                        : This will only Enable the MSMQ HTTP Feature. This will fail if there are
                            :   dependencies on a parent feature that are not enabled.

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

There are parent features that need to enabled.  By default the include parent value
is set to enable these prerequisites.

Example Playbook
----------------

    - hosts: servers
      roles:
         - ctxcommunity.windows.msmq_http

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
