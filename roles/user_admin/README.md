# danielfdickinson.system_base_debian.user_admin

Convenience role for [Daniel F. Dickinson](https://www.wildtechgarden.ca/about/)
that adds or updates admin user.

## Requirements

Uses `ansible.builtin.user`, `ansible.builtin.template`, and
`ansible.builtin.file`.

## Role Variables

### Required to be passed in

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| new_admin_password |                          | n/a                          |

### Optional to be passed in

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| new_comment        |                          | n/a                          |
| new_admin_ssh_key  |                          | n/a                          |

* `no-agent-forwarding,no-port-forwarding` will be prepended to
	`new_admin_ssh_key` when writing to `authorized_keys`.

* For legacy use `admin_gecos` will be used if present and `new_comment` is not
provided.

### Overridable defaults

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| new_base_homedir   | `/home`                  | defaults                     |
| new_admin_user     | `admin`                  | defaults                     |

## Dependencies

`apparmor_homedir` in this collection.

## Example Playbook

``` yaml
- hosts: all
  roles:
  - role: danielfdickinson.system_base_debian.user_admin
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
