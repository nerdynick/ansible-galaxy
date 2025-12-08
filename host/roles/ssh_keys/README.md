# nerdynik.host ssh_keys Role

A role to help install Authorized SSH Keys for a single user on a host.
It can load public keys from a local file path, raw strings, and 1Password.

## Role Variables

```yaml
ssh_keys_user: ""
ssh_keys_public_keys: []
ssh_keys_public_keys_paths: []
ssh_keys_one_password:
  - uuid: ""
    vault: ""
    field: ""
```

## Example Playbook

```yml
- name: Installing Sublime Text
  ansible.builtin.include_role:
    name: nerdynik.host.ssh_keys
  vars:
    ssh_keys_user: ubuntu
    ssh_keys_public_keys: 
      - ssh-rsa adhaklhdakjhdaklshdkla=
    ssh_keys_public_keys_paths:
      - ~/.ssh/public.key
    ssh_keys_one_password:
      - uuid: ajdhliuehqriuwhviuhasdkjh8
        vault: MyVault
        field: public key
```

## Role Idempotency

True

## Argument Specification

Including an example of how to add an argument Specification file that validates the arguments provided to the role.

```yaml
argument_specs:
  main:
    short_description: Role description.
    options:
      string_arg1:
        description: string argument description.
        type: "str"
        default: "x"
        choices: ["x", "y"]
```

## License

BSD-3-Clause

## Author Information

Originally Created by [NerdyNik](https://github.com/nerdynick/)
