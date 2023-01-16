# danielfdickinson.system_base_debian.apt_add_non_free

Convenience role for [Daniel F. Dickinson](https://www.wildtechgarden.ca/about/)
adds contrib and non-free for the apt sources in a base Debian cloud image.

## Requirements

The default (main only) sources for a generic Debian cloud image. (This has
the main archive, the security archive, updates, and backports).

## Role Variables

### Recommended to be passed in

N/A

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
  - role: danielfdickinson.system_base_debian.apt_add_non_free
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
