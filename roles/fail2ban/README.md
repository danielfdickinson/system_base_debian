# danielfdickinson.system_base_debian.fail2ban

Convenience role for [Daniel F. Dickinson](https://www.wildtechgarden.ca/about/)
that configures a fairly stock [fail2ban](https://www.fail2ban.org/) setup,
mostly using upstream defaults (except that jails are enabled, and some ports
can be changed to reflect the ports actually used).

## Requirements

When using the defaults (no override of `f2b_jails`), then this module expects
that `ansible_ssh_port` is defined and a valid port.

Expects `remote_ignore_ips` to be a list of ipv4 and/or ipv6 addresses which are
not to be blocked even if they trigger a rule. Usually you will want this to be
the IP address of the ansible control node, as seen by the host. If using OVH
dedicated server real-time monitoring, you may also wish to include the service
monitoring IP address(es) that access actual service ports (that is not the
icmp/icmp6 only monitoring addresses).

## Role Variables

### Recommended to be passed in

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| f2b_jails          | [{port: "{{ ansible_ssh_port }}"}] | defaults           |
| remote_ignore_ips  | []                       | global                       |

See below

### Overridable defaults

N/A

### Overridable vars

N/A

### Structure of `f2b_jails`

```yaml
# if dest is ssh, dovecot, mx, or haproxy you cannot specify content as it will
# use a jail configuration defined in the `extra_jail.local.j2` tempalate
- dest: string
  port: string (optional) # may be a valid `fail2ban` port string
  port_extra: string (optional) # as port, but only for the sieve part of the
  # dovecot jail configuration defined in `extra_jail.local.j2`
  content: string # should be a multi-line string when dest is not one of the
  # predefined jails mentioned above. This will be written out as the
  # `{{ dest }}.local` `fail2ban` config in `/etc/fail2ban/jail.d` directory.
- dest: another-string # and so on. Only one jail is required at any one time
  # using the role.
```

## Dependencies

N/A

## Example Playbook

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

``` yaml
- hosts: all
  roles:
  - role: danielfdickinson.system_base_debian.fail2ban
    f2b_jails:
    - dest: haproxy
      port: 3832
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
