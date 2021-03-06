# Ansible-Grafana

Installs Grafana Server, configurations and backup scripts

<!-- MarkdownTOC -->

- Dependencies
- Requirements
- Role Variables
    - defaults/main.yml
- Example Playbook
- ```yaml
- License
- Author Information

<!-- /MarkdownTOC -->


## Dependencies
None

## Requirements
None

## Role Variables

### defaults/main.yml
```yaml
data_mount_root: "/data"
backup_directory: "backups"

grafana_install_from_repo: True
grafana_install_release: stable
grafana_install_verion: 5.4.2
grafana_template_configuration: True
grafana_enable_auth_ldap: False
grafana_enable_auth_google: False
grafana_enable_auth_basic: False
grafana_enable_auth_github: False
grafana_enable_auth_oauth: False
grafana_enable_auth_grafana: False
grafana_enable_auth_proxy: False
grafana_enable_auth_anonymous: False
grafana_data_dir: /var/lib/grafana
grafana_configuration_dir: /etc/grafana
grafana_http_protocol: http
grafana_http_addr: 0.0.0.0
grafana_http_port: 3000
grafana_domain:
grafana_root_url:
grafana_enable_gzip: True
grafana_url: http://localhost:3000
grafana_enable_backups: True
grafana_backup_dir: "{{ data_mount_root }}/{{ backup_directory }}/grafana"
grafana_backup_tool_dir: /usr/local/src/grafana-backup-tool
grafana_api_token:

grafana_enable_smtp: False
grafana_smtp_host:
grafana_smtp_port:
grafana_smtp_user:
grafana_smtp_password:
grafana_smtp_cert_file:
grafana_smtp_key_file:
grafana_smtp_skip_verify: False
grafana_smtp_from_address:
grafana_smtp_from_name:
grafana_smtp_ehlo_identity:


# OpenLDAP Variables (usually already defined in group_vars when using openldap role)

openldap_server_ip:
openldap_server_rootpw: "{{ vault_openldap_server_rootpw }}"
openldap_server_enable_ssl: false

grafana_enable_ssl: False
ssl_certpath:
ssl_keypath:
ssl_privkey:
ssl_certchain:
```

## Example Playbook
```yaml
---
- name: Grafana Server
  hosts: grafana
  become: True
  tasks:
    - import_role:
        name: common
    - import_role:
        name: grafana

```

## License

MIT

## Author Information

Created by Alan Janis

