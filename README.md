# Ansible role: burp-server
Graham Keeling's backup software.
This role is for a server that will receive backups from
remote [clients](https://github.com/ho-ansible/burp).

## Requirements
Only tested on Debian stable, for now.

## Role Variables
+ `burp_iface` (default: auto-selected): network interface to bind
  the systemd service to
+ `burp_user` (default: burp): unprivileged user to run server as
+ `burp_data_dir` (default: /var/burp): where to store backups
+ `burp_pid_dir` (default: /var/run/burp): where to store PID lockfile
+ `burp_ca_name` (default: burp): Certificate Authority that signs client certs
+ `burp_restore_clients`: list of clients allowed to manage the server
+ `burp_dhparams`: Diffie-Helman parameters for encryption.
  Generate with, e.g., `openssl dhparam 2048 -5`
+ `burp_offsite`: where cronjob will rsync `burp_data_dir` to.
  This is intended to be a remote (NFS, sshfs, NBD, iSCSI) mount.

## Dependencies
+ [ho-ansible.burp](https://github.com/ho-ansible/burp)

## Example Playbook

```
- hosts: backup
  roles:
    - { role: ho-ansible.burp-server }
```

## License
+ burp is licensed [AGPLv3](https://burp.grke.org/licence.html).
+ This ansible role is licensed [MIT](LICENSE).

## Author Information
+ burp is by [Graham Keeling](http://burp.grke.org/)
+ This ansible role is by [Sean Ho](https://github.com/ho-ansible/)

