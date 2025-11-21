# nerdynik.workstation sublime_text Role

This role installs Sublime Text on either MacOS or Debian/Redhat like Linux Distros.
It will take care of installing the Cask in the case of MacOS
or adding the GPG Signing Key, Repo, and Package in the case of Linux.


## Dependencies

Leverages the role `nerdynik.general.multiplatform_installer` from the `nerdynik.general` collection.

## Example Playbook

```yaml
- name: Installing Packages
  hosts: servers
  roles:
    - role: nerdynik.general.sublime_text
```

```yaml
- name: Installing Packages
  hosts: servers
  gather_facts: false
  tasks:
    - name: Installing Sublime Text
      ansible.builtin.include_role:
        name: nerdynik.general.sublime_text
```

## Role Idempotency

Role is Idempotency

## Author Information

Originally Created by [NerdyNik](https://github.com/nerdynick/)
