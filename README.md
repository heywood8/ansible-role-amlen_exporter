# ansible-role-amlen_exporter
[![CI](https://github.com/heywood8/ansible-role-amlen_exporter/workflows/CI/badge.svg?event=push)](https://github.com/heywood8/ansible-role-amlen_exporter/actions?query=workflow%3ACI)
This role installs Prometheus' [Amlen exporter](https://github.com/heywood8/amlen-prometheus-exporter) on Linux hosts, and configures a systemd unit file so the service can run and be controlled by systemd.
## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    amlen_exporter_version: 0.4.0

The version of Node exporter to install. Available releases can be found on the [tags](https://github.com/heywood8/amlen-prometheus-exporter/tags) listing in the Amlen exporter repository.

If you change the version, the `amlen_exporter` binary will be replaced with the updated version, and the service will be restarted.

    amlen_exporter_arch: 'amd64'
    amlen_exporter_download_url: "{{ amlen_exporter_download_prefix }}/{{ amlen_exporter_version }}/amlen_exporter-{{ amlen_exporter_version }}.centos7-{{ amlen_exporter_arch }}.tar.gz"

The architecture and download URL for Node exporter.

    amlen_exporter_bin_path: /usr/local/bin/node_exporter

The path where the `amlen_exporter` binary will be installed.

    amlen_exporter_port: 9672

Port on which node exporter will listen.

    amlen_exporter_user: amlen_exporter

User which will run the `amlen exporter`

    amlen_exporter_target: localhost:9089

Adress of Amlen server to get metrics from

    amlen_exporter_state: started
    amlen_exporter_enabled: true

Controls for the `amlen_exporter` service.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - role: heywood.node_exporter

## License

MIT / BSD

## Author Information

This role was created in 2023 by [Nikita Lopatin](https://github.com/heywood8/).
