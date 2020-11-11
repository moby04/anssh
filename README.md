# AnSSH

`anssh` is an ssh connection management utility written by Dmitry Dunaev.
It can be downloaded directly from Github repository at `https://github.com/JustDolanIt/anssh`

It parses Ansible inventories to establish SSH connection with servers.

## Setup 

### Dependencies

- Python 3
- Click 7.0
- PyYaml 5.1.2

Python dependencies can be installed with pip: `pip install -r <path-to-repository>/requirements.txt`

### Actual tool setup

1. Clone repository
2. Create main configuration file `~/.anssh` containing list of inventory files
    ```yaml
    default:
        user: <DEFAULT_USERNAME>
        ssh_key: <DEFAULT_SSH_KEY>
    
    namespaces:
      - name: <NAMESPACE>
        clients:
          - name: <GROUP_NAME>
            hosts_path: <PATH_TO_INVENTORY_FILE>
    ```
3. Ensure you have proper inventory files pointed out by above configuration
4. Add `anssh` from main repository's to your `PATH` variable

## Usage

```bash
anssh connect <NAMESPACE> <GROUP> <HOSTNAME_WITHIN_INVENTORY_FILE>

## TODO

- [ ] Write usable README
- [ ] Integrate with SetupTools (https://click.palletsprojects.com/en/7.x/setuptools/)
- [x] Optimize work by deleting files to list to dict cycle by changing it to files to dict
- [x] Catch all KeyError exceptions
- [x] Honour ansible_user
- [x] Honour ansible_ssh_common_args
- [x] Honour ansible_ssh_private_key
- [ ] And passing of optional ssh params available on connect (-A / -L for example)

