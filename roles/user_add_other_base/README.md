# danielfdickinson.system_base_debian.user_add_other_base

Convenience role for [Daniel F. Dickinson](https://www.wildtechgarden.ca/about/)
that adds or updates a user which may have an alternate base homedir and may
accept incoming SSH.

## Requirements

TBD

## Role Variables

### Recommended to be passed in

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|

### Overridable defaults

TBD

### Overridable vars

TBD

## Dependencies

TBD

## Example Playbook

``` yaml
- hosts: all
  roles:
  - role: danielfdickinson.system_base_debian.user_add
    name: libvirt-client
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
