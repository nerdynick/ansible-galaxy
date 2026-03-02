# nerdynik.host hostname Role

A role to set the hostname for the machine, including via temp means as to not require reboot.

## Role Variables

```yaml
hostname_ip: 127.0.1.1 # Debian default address. See https://askubuntu.com/questions/754213/what-is-difference-between-localhost-address-127-0-0-1-and-127-0-1-1
hostname_fqdn: "" # The Fully Qualified Domain to set as the Hostname
hostname_pretty: "" # An optional shorter/prettier name to use within the host
```

## Example Playbook



## Role Idempotency

True

## License

BSD-3-Clause

## Author Information

Originally Created by [NerdyNik](https://github.com/nerdynick/)