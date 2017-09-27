# Ansible Role: prometheus-rabbitmq-exporter

An Ansible role that installs Prometheus Node Exporter on Ubuntu|Debian-based machines with systemd.

Based off the role by UnderGreen: https://github.com/UnderGreen/ansible-prometheus-node-exporter

## Requirements

All needed packages will be installed with this role.

## Role Variables

Available variables are listed below, along with default values:
```yaml
prometheus_rabbitmq_exporter_version: 0.20.0
prometheus_rabbitmq_exporter_release_name: "rabbitmq_exporter-{{ prometheus_rabbitmq_exporter_version }}.linux-amd64"
url: "https://github.com/kbudde/rabbitmq_exporter/releases/download/v{{ prometheus_rabbitmq_exporter_version }}/{{ prometheus_rabbitmq_exporter_release_name }}.tar.gz"

prometheus_rabbitmq_exporter_config_flags:
  'rabbit_url': 'http://localhost:15672'
  'rabbit_user': 'guest'
  'rabbit_password': 'guest'
  'rabbit_user_file': ''
  'rabbit_password_file': ''
  'publish_port': '9090'
  'output_format': 'TTY'
  'log_level': 'info'
  'cafile': 'ca.pem'
  'skipverify': 'false'
  'include_queues': '.*'
  'skip_queues': '^$'
  'rabbit_capabilities': 'no_sort,bert'
  'rabbit_exporter': 'exchange,node,overview,queue'
```
## Dependencies

- UnderGreen.prometheus-exporters-common

## Example Playbook
```yaml
- hosts: node-exporters
  roles:
    - nwalke.prometheus-rabbitmq-exporter
  vars:
    prometheus_rabbitmq_exporter_config_flags:
      'rabbit_url': 'http://rabbithost:15672'
```
## License

GPLv2
