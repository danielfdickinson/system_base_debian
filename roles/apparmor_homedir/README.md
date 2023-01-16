# danielfdickinson.system_base_debian.apparmor_homedir

Convenience role for [Daniel F. Dickinson](https://www.wildtechgarden.ca/about/)
that updates apparmor for non-stock admin homedir.

## Requirements

Assumes that `apparmor` is already installed and enabled in enforcing mode. This
role is not necessary if such is not the case.

## Role Variables

### Recommended to be passed in

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| aa_base_homedir    | `/home`                  | defaults                     |

It is expected (since 'silly' otherwise) that `aa_base_homedir` will be
overridden.

### Overridable defaults

N/A

### Overridable vars

N/A

## Dependencies

N/A

## Example Playbook

``` yaml
- hosts: all
  roles:
  - role: danielfdickinson.system_base_debian.apparmor_homedir
    aa_base_homedir: /admin-home
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
