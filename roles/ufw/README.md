# danielfdickinson.system_base_debian.ufw

Convenience wrapper around `community.general.ufw` that loops over provided
rules (with sensible defaults to reduce required data entry), and which enables
basic (low) logging but omitting the logging ipv4 multicast blocks (because that
is very common and spams the logs with pointless messages).

## Requirements / Expectations

By default expects `ansible_ssh_port` to be set and that the user wants that
port to be allowed in from anywhere.

Since this role depends on `community.general.ufw`, this role will will install
the `ufw` package using apt, if `ufw` is not already installed.

This role is only designed for a fairly simple allowing of tcp and/or udp ports
to come into the host. It is more a macro than a full role.

## Role Variables

### Recommended to be passed in

|      Variable      | Default                  | Location                     |
|--------------------|------------- ------------|------------------------------|
| ansible_ssh_port   | 22                       | global variables             |
| ufw_added_rules    | \[]                      | defaults                     |

### Overridable defaults

|      Variable      | Default                  | Location                     |
|--------------------|------------- ------------|------------------------------|
| ufw_common_rules   | \[port: {{ ansible_ssh_port }}] | defaults              |

### Overridable vars

| ufw_rules          | \[ufw_common_rules, ufw_added_rules] \| flatten | vars  |

### Default rules

For each rules passed in through ufw_*_rules the following defaults are used:

```yaml
direction: in
from_ip: "{{ from | default('any') }}"
interface: "{{ interface }}"
proto: "{{ proto | default('tcp') }}"
rule: allow
to_ip: "{{ to | default('any') }}"
to_port: "{{ port }}"
```

## Dependencies

* Depends on the `community.general` collection `ufw` module

## Example Playbook

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

``` yaml
- hosts: webservers
  roles:
  - role: danielfdickinson.system_base_debian.ufw
    ufw_added_rules:
    - port: 80
    - port: 443
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
