# danielfdickinson.system_base_debian.dfd_base_misc

Convenience role for [Daniel F. Dickinson](https://www.wildtechgarden.ca/about/)
that configures some miscellaneous settings for his baseline for hosts.

## Requirements

Assumes that an admin user (the ansible ssh user) exists, has the same group
as the user name, and has a home directory with ${admin_base_homedir} as the
prefix for a sub-directory with the same name as the admin user (that is
${admin_base_homedir}/${admin_user} is the admin user's home directory).

## Role Variables

### Recommended to be passed in

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| admin_base_homedir | /home                    | defaults                     |
| admin_user         | admin                    | defaults                     |

### Overridable defaults

No additional variables

### Overridable vars

No additional variables

## Dependencies

N/A

## Example Playbook

``` yaml
- hosts: all
  roles:
  - role: danielfdickinson.system_base_debian.dfd_base_misc
    admin_user: anadmin
    admin_base_homedir: /admin-homes
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
