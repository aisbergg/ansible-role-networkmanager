# Ansible Role: `aisbergg.networkmanager`

This Ansible role is used to install and configure NetworkManager, and also manage network connections on Debian, RedHat and Arch Linux distributions.

## Requirements

None.

## Role Variables

| Variable | Default  | Comments |
|----------|----------|----------|
| `networkmanager_redhat_enablerepo` |  | Repository to enable while installing NetworkManager. Applies only to RedHat systems. |
| `networkmanager_debian_repo` | `{{ ansible_distribution_release }}-backports` | Repository used for installation. Applies only to Debian systems. |
| `networkmanager_extra_packages` | `[]` | List of additional packages to be installed, e.g. `wireguard`. |
| `networkmanager_service_enabled` | `true` | Enable the NetworkManager service. |
| `networkmanager_service_state` | `started` | Manage the state of the NetworkManager service</br>Choices: <ul><li>reloaded</li><li>restarted</li><li>started</li><li>stopped</li></ul> |
| `networkmanager_service_restart_on_change` | `true` | Restart NetworkManager service on configuration changes. |
| `networkmanager_connections` | `[]` | List of network connections. The parameters can be looked up [here](https://docs.ansible.com/ansible/latest/collections/community/general/nmcli_module.html). |
| `networkmanager_config` | `{}` | Main NetworkManager configuration. Available options can be found in the [NetworkManager.conf.5](https://man.archlinux.org/man/NetworkManager.conf.5.en) manpage. The options need to be provided as key-value pairs. See Example Section below for the correct syntax. |
| `networkmanager_conf_d` | `{}` | List of NetworkManager configurations, that will be put into the `conf.d/` directory. See Example Section below for the correct syntax. |

## Dependencies

Depends on `community.general` collection.

## Example Playbook

```yaml
- hosts: all
  vars: 
    vars:
      networkmanager_service_enabled: true
      networkmanager_service_state: started
      
      networkmanager_config:
        logging:
          level: WARN
          domains: ALL

      networkmanager_conf_d:
        "mac-address":  # -> conf.d/mac-address.conf
          "device-mac-randomization":
            # "yes" is already the default for scanning
            "wifi.scan-rand-mac-address": true

          "connection-mac-randomization":
            # Randomize MAC for every ethernet connection
            "ethernet.cloned-mac-address": random
            # Generate a random MAC for each WiFi and associate the two permanently.
            "wifi.cloned-mac-address": random
      
      networkmanager_connections:
        # set DNS resolvers on default interface
        - name: "{{ ansible_default_ipv4.interface }}"
          type: "{{ 'ethernet' if ansible_default_ipv4.type == 'ether' else omit }}"
          dns4: ['9.9.9.9']
          dns4_search: example.org

  roles:
    - aisbergg.networkmanager
```

## License

MIT

## Author Information

Andre Lehmann (aisberg@posteo.de)
