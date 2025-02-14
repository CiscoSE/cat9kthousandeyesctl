# cat9kthousandeyesctl

Deploy Cisco Thousand Eyes agent on Cisco Catalyst 9000

```
cat9kthousandeyesctl deploy -c config.yaml  
Deploying Thousand Eyes Agents
100.118.1.71:   Thousand eyes agent deployed  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:02:15
100.118.1.69:   Thousand eyes agent deployed  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:02:13
100.118.1.81:   Thousand eyes agent deployed  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:02:14
```

```
cat9kthousandeyesctl status -c config.yaml            
Collecting status of Thousand Eyes Agents
100.118.1.71:   Status completed  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:00:03
100.118.1.69:   Status completed  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:00:03
100.118.1.81:   Status completed  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 0:00:03
                                                                         
                       Status Thousand Eyes Agents                       
┏━━━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ Host         ┃ Hardware   ┃ Subscription  ┃ Version  ┃ Iox  ┃ Apps                          ┃
┡━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│ 100.118.1.71 │ C9300-24UX │ dna-advantage │ 17.03.03 │ True │ thousandeyes_enterprise_agent │
│ 100.118.1.69 │ C9300-24UX │ dna-advantage │ 17.03.03 │ True │ thousandeyes_enterprise_agent │
│ 100.118.1.81 │ C9300-24UX │ dna-advantage │ 17.03.03 │ True │ thousandeyes_enterprise_agent │
└──────────────┴────────────┴───────────────┴──────────┴──────┴───────────────────────────────┘
```

## Prerequisites
- Network connectivity
    - Internet
    - DNS
    - DHCP
- Cisco Thousand Eyes Account
    - Token
- Cisco Catalyst 9000
    - C9300
    - C9400
- Cisco IOS-XE Software
    - 17.3.3+
- ```netconf-yang``` enabled
- Python 3
  - Version: 3.7+

## Installation

### Python Package Index (PyPI)
```pip install cat9kthousandeyesctl```

```cat9kthousandeyesctl --help```

### Config
Download [config.yaml](./config.yaml) sample config

### Deploy
```cat9kthousandeyesctl deploy --config config.yaml```

### Status
```cat9kthousandeyesctl status --config config.yaml```

### Undeploy (remove)
```cat9kthousandeyesctl undeploy --config config.yaml```

## Features

Include a succinct summary of the features/capabilities of your project.

- [x] Deploy
- [x] Status
- [x] Undeploy
- [x] YAML Config
    - VLAN
    - Agent Download URL
- [x] Interactive mode (prompt)

## Technologies & Frameworks Used

**Cisco Products & Services:**

- Cisco Catalyst 9000
- Cisco Thousand Eyes

**Tools & Frameworks:**

- Python
    - click
    - ncclient
    - rich
- Docker

## Usage

```
Usage: cat9kthousandeyesctl [OPTIONS] COMMAND [ARGS]...

  Manage Thousand Eyes Agent on Catalyst 9000

Options:
  --version  Show the version and exit.
  --debug    Enable logging
  --help     Show this message and exit.

Commands:
  deploy       Deploy Thousand Eyes Agent
  interactive  Interactive TTY mode
  status       Status of Application Hosting on the devices
  undeploy     Remove Thousand Eyes Agent
```

## Config

```
# Netconf Settings
username: admin
password: password
port: 830
timeout: 600

# Thousand Eyes Agent Settings
download_url: https://downloads.thousandeyes.com/enterprise-agent/thousandeyes-enterprise-agent-3.0.cat9k.tar
appid: thousandeyes_enterprise_agent
vlan: 1
token: thousand_eyes_token

# Devices to manage
hosts:
  192.168.1.1:
  192.168.1.2:
    vlan: 100 # Override global vlan
  10.0.0.1:
    vlan: 200
  10.0.0.2:
    vlan: 200
```

## Authors & Maintainers

- Robert Csapo <rcsapo@cisco.com>

## License

This project is licensed to you under the terms of the [Cisco Sample
Code License](./LICENSE).
