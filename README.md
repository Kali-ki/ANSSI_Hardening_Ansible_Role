Role Name
=========

This Ansible role configures a Linux system to follow [ANSSI recommendations](https://messervices.cyber.gouv.fr/guides/recommandations-de-securite-relatives-un-systeme-gnulinux).

WARNING: It establishes rules that restrict conventional use.

Please note that certain rules cannot be or are not applied

- "E" level protection ARE NOT APPLYED : R4, R6, R15 to R27, R46, R47, R48, R49, R66, R76, R77

- R28 has be done during system installation
- R1, R2, R3, R5 should be done on BIOS
- NOT AUTOMABLE: R30, R33, R34, R35, R38, R39, R40, R41, R42, R43, R44, R50, R52, R53, R54, R55, R56, R57, R58, R59, R60, R62, R63, R64, R65, R68, R69, R70, R74, R75, R78, R79, R80

- TODO: R37, R45, R71, R72

Requirements
------------

The system has be partionned like:

- /
- /boot
- /opt
- /srv
- /home
- /usr
- /var
- /var/log
- /var/tmp

[A compitable preseed is available](debian_preseed_anssi.cfg).

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml)

Dependencies
------------

Example Playbook
----------------

```
- name: Deploy security on firewall
  hosts: firewall

  roles:
    - role: anssi_debian_recommandations
      vars:
        # Is the system boot with UEFI
        anssi_debian_recommandations_uefi: true
        anssi_debian_recommandations_is_router: true
        anssi_debian_recommandations_auditd_kernel_panic: true
```

License
-------

MIT Licence

Author Information
------------------

Kikack
