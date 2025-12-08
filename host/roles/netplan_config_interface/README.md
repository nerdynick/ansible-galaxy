# nerdynik.host netplan_config_interface Role

A role to adjust netplan configs to configure DHCP & Static IP information. As well as DNS settings.

## Requirements

This role makes use of the [kwoodson.yedit](https://github.com/kwoodson/ansible-role-yedit) role/module for editing the Netplan YAML configs.

## Role Variables

```yaml
netplan_config_interface_interface: ""
netplan_config_interface_netplanfile: "/etc/netplan/50-cloud-init.yaml"

netplan_config_interface_dns4_addresses:
  - 1.1.1.1
  - 1.0.0.1

netplan_config_interface_dhcp4: false
netplan_config_interface_ip4_addresses: []
netplan_config_interface_ip4_routes: []
```

## Dependencies

This role makes use of the [kwoodson.yedit](https://github.com/kwoodson/ansible-role-yedit) role/module for editing the Netplan YAML configs.

## Example Playbook



## Role Idempotency

True

## License

BSD-3-Clause

## Author Information

Originally Created by [NerdyNik](https://github.com/nerdynick/)