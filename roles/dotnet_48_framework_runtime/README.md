Role Name
=========

Role Name: ctxcommunity.windows.dotnet_48_framework_runtime

This role installs and removes the Windows Feature .NET 4.8 Framework Runtime

Requirements
------------

No pre-requisites.

Role Variables
--------------

The defaults/main.yml contains the following variable and default value

  win_feature_dotnet_framework_48_runtime_state: present

The win_feature_dotnet_framework_48_runtime_state variable controls the installation state
for the Windows Feature .NET 4.8 Framework Runtime

Possible Values are:
  present         (default) : This will install the NET 4.8 Framework Runtime
  absent                    : This will remove the NET 4.8 Framework Runtime

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
         - ctxcommunity.windows.dotnet_48_framework_runtime

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
