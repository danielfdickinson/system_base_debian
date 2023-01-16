# danielfdickinson.system_base_debian.firmware_install

Convenience role for [Daniel F. Dickinson](https://www.wildtechgarden.ca/about/)
makes sure linux kernel firmware and cpu microcode is installed from non-free,
and reboots the host if a new install occurs (since microcode and most firmware
are not applied until a new boot occurs).

## Requirements

Same as apt_add_non_free role, on which this role depends

## Role Variables

N/A

### Overridable defaults

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| firmware_extra     | []                       | defaults                     |

`firmware_extra` is meant for additional Debian firmware packages to install
(for example `firmware-realtek` on systems with realtek network cards).

### Overridable vars

N/A

## Dependencies

Depend on apt_add_non_free role in this collection (so
`danielfdickinson.system_base_debian.apt_add_non_free`).

## Example Playbook

``` yaml
- hosts: all
  roles:
  - role: danielfdickinson.system_base_debian.firmware_install
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
