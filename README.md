# Ansible Role: firefox

[![Pre-Commit](https://github.com/cowdogmoo/ansible-firefox/actions/workflows/pre-commit.yaml/badge.svg)](https://github.com/cowdogmoo/ansible-firefox/actions/workflows/pre-commit.yaml)
[![Molecule Test](https://github.com/cowdogmoo/ansible-firefox/actions/workflows/molecule.yaml/badge.svg)](https://github.com/cowdogmoo/ansible-firefox/actions/workflows/molecule.yaml)
[![Ansible Galaxy](https://img.shields.io/badge/Galaxy-cowdogmoo.firefox-660198.svg?style=flat)](https://galaxy.ansible.com/cowdogmoo/firefox)
[![License](https://img.shields.io/github/license/CowDogMoo/ansible-firefox?label=License&style=flat&color=blue&logo=github)](https://github.com/CowDogMoo/ansible-firefox/blob/main/LICENSE)

This role installs [firefox](https://www.mozilla.org/en-US/firefox/new/)
on Ubuntu hosts.

## Requirements

- Python packages

  Install with:

  ```bash
  python3 -m pip install --upgrade molecule-docker
  ```

---

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

Path to `python3` interpreter on the target system.

```yaml
ansible_python_interpreter: /usr/bin/python3
```

**Debian-specific vars:**

Required packages for the installation.

```yaml:
install_packages:
  - dirmngr
```

---

## Dependencies

None.

---

## Example Playbook

```yaml
---
- name: Example playbook
  hosts: all
  become: true
  environment:
    DEBIAN_FRONTEND: noninteractive
  roles:
    - role: cowdogmoo.firefox
```

---

## Local Development

Make sure to run the following to develop locally:

```bash
PATH_TO_ROLE="${PWD}"
ln -s "${PATH_TO_ROLE}" "${HOME}/.ansible/roles/cowdogmoo.firefox"
```

---

## Testing

To test changes made to this role, run the following commands:

```bash
molecule create
molecule converge
molecule idempotence
# If everything passed, tear down the docker container spawned by molecule:
molecule destroy
```
