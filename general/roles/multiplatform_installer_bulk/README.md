# nerdynik.general multiplatform_installer_bulk Role

A simple role to install a collection of packages via native package managers; Brew, Apt, Yum, Dnf, etc.
Allows for a multi-platform installation of collections. To ensure different platforms have similar installations.


## Role Variables

```yaml
multiplatform_installer_bulk_packages_mac: []
multiplatform_installer_bulk_packages_mac_casks: []
multiplatform_installer_bulk_packages_linux: []
multiplatform_installer_bulk_packages_linux_apt: []
multiplatform_installer_bulk_packages_linux_yum: []
```

## Example Playbook

```yml
- name: Installing Packages
  ansible.builtin.include_role:
    name: nerdynik.general.multiplatform_installer_bulk
  vars:
    multiplatform_installer_bulk_packages_mac: []
    multiplatform_installer_bulk_packages_mac_casks: []
    multiplatform_installer_bulk_packages_linux: []
    multiplatform_installer_bulk_packages_linux_apt: []
    multiplatform_installer_bulk_packages_linux_yum: []
```

## Role Idempotency

True

## License

BSD-3-Clause

## Author Information

Originally Created by [NerdyNik](https://github.com/nerdynick/)
