# Ansible Role: Deploy HAProxy

[![Build Status](https://travis-ci.org/dsgnr/ansible-role-deploy-haproxy.svg?branch=master)](https://travis-ci.org/dsgnr/ansible-role-deploy-haproxy)

This role installs HAProxy on Ubuntu and RHEL/CentOS machines. A Fail2Ban configuration is also included for detecting Unifi Controller fialed login attempts.

Your HAProxy configuration is to be stored in `templates/{{inventory_hostname}}/haproxy.cfg`. This is not dynamically created at this time.
 
## Requirements

None.

## Role Variables

None.

## Dependencies

None.

## Example Playbook

    - hosts: all
      become: true
      
      roles:
        - deploy-haproxy

## License

GNUv3

## Author Information

This role was created by [Dan Hand](https://danielhand.io).

