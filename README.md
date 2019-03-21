# Ansible role for PostgreSQL

[![CircleCI](https://circleci.com/gh/angristan/ansible-postgresql.svg?style=svg)](https://circleci.com/gh/angristan/ansible-postgresql)

This is a simple role that will install PostgreSQL and handle users, databases and configuration.

The role should work on all Debian-based distributions.

By default, the role will install PostgreSQL 11 from the [PGDG APT repository](https://wiki.postgresql.org/wiki/Apt). You can set a version with `postgresql_version`.

## Sample playbook

```yaml
---

- hosts: myhost
  roles:
    - name: postgresql
      tags: postgresql
  vars:
    postgresql_version: 11
    postgresql_install_from_pgdg: true
    postgresql_options:
      - key: listen_addresses
        value: "'*'"
    postgresql_databases:
      - name: blog
    postgresql_users:
      - name: blog
        password: "{{ vault_postgresql_password_blog }}"
        db: blog
```
