# danielfdickinson.system_base_debian.network_hosts_file

Convenience role to manage cloud-init managed `/etc/hosts` file to ensure
correct address to and from fqdn mapping, as well as support other desired
mappings of an ip/ip6 address and a hostname/fqdn (of other hosts).

## Requirements / Expectations

Requires that `/etc/hosts` is managed by `cloud-init` and that the hostname and
fqdn have been properly set.

## Role Variables

### Overridable defaults

|      Variable      | Default                  | Location                     |
|--------------------|--------------------------|------------------------------|
| hostname_aliases   | []                       | defaults                     |
| instance_fqdn      | {{ ansible_facts\['fqdn'] }} | defaults                  |
| instance_hostname  | {{ ansible_facts\['hostname'] }} | defaults              |
| instance_v4addr  | {{ ansible_facts\['default_ipv4']\['address'] }} | defaults |
| instance_v6addr    | see below                | defaults                     |
| localhost_aliases  | []                       | defaults                     |

* `instance_v6addr` defaults to `"{{ ansible_facts['default_ipv6']['address'] | default(local_ipv6_addr) | default(null) }}"`
	* local_ipv6_addr is best ultimately defined per-host via inventory variables
* localhost_aliases is a list of strings that will be appended to the
	`127.0.0.1` and `::1` lines.

#### Structure of `hostname_aliases`

```yaml
- hostnames:
  - host1fqdn
  - host1
  - …
  v4addr: 1.2.3.4
  v6addr: 1:2:3::4
- hostnames:
  - host2
  v4addr: 5.6.7.8
  v6addr: 5:6:7:8::9
- …
```

## Dependencies

N/A

## Example Playbook

Set fqdn and hostname of all hosts to match real ipv4 and/or ipv6 of the host

``` yaml
- hosts: all
  roles:
  - role: danielfdickinson.system_base_debian.network_hosts_file
```

By setting inventory host variables you can also define per-host additional
localhost aliases and/or additional ip/ip6 hostname mappings.

For example, by settings `host_vars/host3.domain.tld/vars.yml` to include:

```yaml
hostname_aliases:
- hostnames:
  - host1
  v4addr: 3.4.5.6
  v6addr: 3:4:5::6
localhost_aliases:
- alias1
- alias2
```

with the above play, all hosts would set the fqdn and hostname to match the
real ipv4 and/or ipv6 of the host and host3 would additionally define localhost
aliases and hostname aliases.

This might look like (snippet of `/etc/hosts` not full file):

```plaintext
127.0.0.1 localhost alias1 alias2
::1 ip6-localhost ip6-loopack alias1 alias2

3.4.5.6 host1

3:4:5::6 host1
```

## License

MIT

## Author Information

Daniel F. Dickinson \<dfdpublic@wildtechgarden.ca>
<https://www.wildtechgarden.ca>
