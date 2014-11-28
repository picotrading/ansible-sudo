sudo
====

Role that manages `/etc/sudoers` through a set of variables.


Example
-------

```
---

# Example of how to use the role
- hosts: myhost
  vars:
    sudo_users:
      # root can run any password
      - root:
          host: ALL
          runas: ALL
          tag: ''
          cmd: ALL
      # wheel group can run any command without password
      - '%wheel':
          host: ALL
          runas: ALL
          tag: NOPASSWD
          cmd: ALL
  roles:
    - sudo
```


Role variables
--------------

List of variables used by the role:

```
# Default host aliases
sudo_host_alias: {}
# Example of host aliases
#sudo_host_alias:
#  FILESERVERS:
#    - fs1
#    - fs2
#  MAILSERVERS:
#    - smtp
#    - smtp2

# Default user aliases
sudo_user_alias: {}
# Example of user aliases
#sudo_user_alias:
#  ADMINS:
#    - jsmith
#    - mikem
#  WEBMASTERS:
#    - peter
#    - lisa

# Default command aliases
sudo_cmd_alias: {}
# Example of command aliases
#sudo_cmd_alias:
#  SOFTWARE
#    - /bin/rpm
#    - /usr/bin/up2date
#    - /usr/bin/yum
#  SERVICES:
#    - /sbin/service
#    - /sbin/chkconfig

# Default sudo defaults
sudo_defaults:
  - requiretty
  - '!visiblepw'
  - always_set_home
  - env_reset
  - env_keep  = "COLORS DISPLAY HOSTNAME HISTSIZE INPUTRC KDEDIR LS_COLORS"
  - env_keep += "MAIL PS1 PS2 QTDIR USERNAME LANG LC_ADDRESS LC_CTYPE"
  - env_keep += "LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES"
  - env_keep += "LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE"
  - env_keep += "LC_TIME LC_ALL LANGUAGE LINGUAS _XKB_CHARSET XAUTHORITY"
  - secure_path = /sbin:/bin:/usr/sbin:/usr/bin

# Default sudo users
sudo_users:
  - root:
      host: ALL
      runas: ALL
      tag: ''
      cmd: ALL
# Example of additional users, groups and aliases
#  - '%wheel':
#      host: ALL
#      runas: ALL
#      tag: NOPASSWD
#      cmd: ALL
#  - ADMINS:
#      host: ALL
#      runas: ''
#      tag: ''
#      cmd: ALL
#  - WEBMASTERS:
#      host: ALL
#      runas: ''
#      tag: ''
#      cmd: SOFTWARE, SERVICES

# Default file includes
sudo_include: []
# Example of file includes
#sudo_include:
#  - /etc/sudoers2

# Default directory includes
sudo_includedir:
  - /etc/sudoers.d
```


License
-------

MIT


Author
------

Jiri Tyr
