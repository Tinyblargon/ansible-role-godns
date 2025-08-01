# Ansible Role: godns

Ansible role to install and configure [GoDNS](https://github.com/TimothyYe/godns)

## Requirements

- N/A

## Dependencies

- N/A

## Role Variables

### Defaults

| **Variable Name**    | **Required**|**Type**| **Default Value**| **Description**|
| :--------------------| :----------:|:------:| :---------------:| :--------------|
| godns_version:       | yes         | string | ""               | The version.|
| godns_config:        | yes         | string | ""               | The content of the configuration for GoDNS. Can be in JSON or YAML.|
| godns_checksum:      | no          | string | ""               | Checksum to validate the binary during download.|
| godns_path:          | no          | string | "/opt/godns"     | The folder in which the application will be installed.|
| godns_service_name:  | no          | string | "godns"          | The name of the system service.|
| godns_wait:          | no          | int    | 5                | Number of seconds to wait while verifying the service started correctly.|
| godns_local_download:| no          | bool   | false            | If `true` the binary will be downloaded by the local machine running the playbook. and then copied to the remote host. If `false` the binary will be downloaded directly from the remote host.|
| godns_state:         | no          | string | "present"        | When `"present"` the GoDNS application will be installed and configured, when `"absent"` the GoDNS application will be removed.|

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: tinyblargon.godns
      vars:
        godns_version: "v3.2.5"
        godns_checksum: "sha256:fe1838be625f61b57f042293924455db5f1e1b5a3944f085a1d5400bc4e02105"
        godns_config: "{{ lookup('file', 'godns_config.yml') }}"
        godns_state: "present"
```

## License

MIT
