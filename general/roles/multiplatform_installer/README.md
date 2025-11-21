# nerdynik.workstation multiplatform_installer Role

A simple role to assist with installing a single application across multiple OSs. 
Currently this supports MacOS and Debian/Redhat like Linux Distros.
It will take care of installing the Homebrew Casks, if needed, in the case of MacOS
or adding the GPG Signing Key, Repo, and Package in the case of Linux.

## Role Variables

### Global Settings
```yml
multiplatform_installer_package: 
```

### Redhat like Linux Settings
```yml
multiplatform_installer_rpm_url: 
multiplatform_installer_yum_package: 
multiplatform_installer_yum_repo: 
   url:
   name:
   key_url:
```

### Debian like Linux Settings
```yml
multiplatform_installer_deb_url: 
multiplatform_installer_apt_package: 
multiplatform_installer_apt_repo: 
   url:
   name:
   dist:
   key_url:
   key_name:
```

### MacOS Settings
```yml
multiplatform_installer_brew_package: 
multiplatform_installer_brew_is_cask: false
```

## Example Playbook

```yml
- name: Installing Sublime Text
  ansible.builtin.include_role:
    name: nerdynik.general.multiplatform_installer
  vars:
    multiplatform_installer_package: sublime-text
    multiplatform_installer_apt_repo:
      name: sublime-text
      url: https://download.sublimetext.com/
      dist: apt/stable/
      key_name: sublimehq-pub
      key_url: https://download.sublimetext.com/sublimehq-pub.gpg
    multiplatform_installer_yum_repo:
      name: sublime-text
      url: https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo
      key_url: https://download.sublimetext.com/sublimehq-rpm-pub.gpg
```

## Role Idempotency

Role is Idempotency

## Author Information

Originally Created by [NerdyNik](https://github.com/nerdynick/)
