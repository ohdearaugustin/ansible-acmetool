Role Name
=========

This role installs and configures the [acmetool](https://github.com/hlandau/acme) on a Debian/Ubuntu server.

Requirements
------------

* OS: Ubuntu 14.04/16.04/18.04

Role Variables
--------------

Default Variables

acmetool_rootless: False
> optional, install acmetool as non-root user

acmetool_user: "acme"
> no-root username

acmetool_email: ""
> optional, let's encypt emails

acmetool_agreement: True
> required, accept terms

acmetool_server: "https://acme-v01.api.letsencrypt.org/directory"
> required

acmetool_method: "proxy"
> required, options: webroot, proxy, stateless, redirector refere to [acmetool](https://hlandau.github.io/acme/userguide#web-server-configuration-challenges) 

acmetool_webroot_path: ""
> required when acmetool_method is webroot

acmetool_quickstart_complete: True

acmetool_systemd_timer: False
> optional, install systemd timer for autorenewal

acmetool_install_cronjob: False
> optinal, install cronjob for autorenewal

acmetool_install_haproxy_script: False
> optional

acmetool_install_redirector_systemd: True
> optional

acmetool_key_type: "rsa"
> required, options: rsa, ecdsa

acmetool_rsa_key_size: 4096
> required, 2048 - 4096 bytes

acmetool_ecdsa_curve: "nistp256"
> required, options: nistp256 (recommended), nistp384, nistp521 (limited support)

Limitations
-----------

* The acmetool method redirector currently is only supported when acmetool is installed as root.
* Either Cronjob or Systemd Timer can be used, but not both at the time.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
        - { role: ansible-acmetool, become: yes }
      vars:
        - acmetool_email: "test@example.com"
        - acmetool_method: "proxy"

License
-------

BSD

Author Information
------------------

Jonas Reindl
