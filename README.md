Ansible role: Prometheus Exporter - Apache
==========================================

Install and configure Apache Exporter for Prometheus.

Requirements
------------

This role depends on the [base prometheus exporter role](https://github.com/wandansible/prometheus_exporter).

Role Variables
--------------

```
ENTRY POINT: main - Install and configure Apache Exporter for Prometheus

OPTIONS (= is mandatory):

- apache_exporter_add_extract_dir
        If true, add an extraction directory for the exporter package
        [Default: False]
        type: bool

- apache_exporter_arch_map
        Mapping of the possible values of ansible_architecture to the
        exporter package architectures
        [Default: (null)]
        type: dict

- apache_exporter_bin_dir
        Directory for the exporter executable
        [Default: (null)]
        type: str

- apache_exporter_binary
        Filename for the exporter executable
        [Default: (null)]
        type: str

- apache_exporter_checksum
        The exporter package checksum
        [Default: (null)]
        type: str

- apache_exporter_checksum_type
        The exporter package checksum type
        [Default: (null)]
        type: str

- apache_exporter_checksums_file
        Filename for the exporter package checksums
        [Default: (null)]
        type: str

- apache_exporter_checksums_url
        URL for the exporter package checksums
        [Default: (null)]
        type: str

- apache_exporter_configure_caddy
        If true, configure caddy to add a TLS endpoint for the
        exporter
        [Default: True]
        type: bool

- apache_exporter_description
        Description for the exporter systemd service
        [Default: (null)]
        type: str

- apache_exporter_extra_flags
        Extra flags to run exporter with
        [Default: (null)]
        type: dict

- apache_exporter_file_sd_dir
        Directory, on scrape servers, for the file service discovery
        target
        [Default: /etc/prometheus/file_sd/apache_exporter]
        type: str

- apache_exporter_flags
        Contents or list of flags to run exporter with
        [Default: (null)]
        type: raw

- apache_exporter_git_org
        Name of organisation for exporter git repository
        [Default: (null)]
        type: str

- apache_exporter_git_repo
        Name of exporter git repository
        [Default: (null)]
        type: str

- apache_exporter_group
        Name of the exporter unix group
        [Default: (null)]
        type: str

- apache_exporter_groups
        Unix groups added to exporter unix user
        [Default: (null)]
        elements: str
        type: list

- apache_exporter_install
        If true, install exporter
        [Default: True]
        type: bool

- apache_exporter_labels
        Labels added to exporter metrics, overrides prometheus_labels
        [Default: (null)]
        type: dict

- apache_exporter_latest_url
        URL for the latest version
        [Default: (null)]
        type: str

- apache_exporter_listen
        Listen address and port
        [Default: localhost:9117]
        type: str

- apache_exporter_log_level
        Only log messages with the given severity or above
        (Choices: debug, info, warn, error)[Default: warn]
        type: str

- apache_exporter_manage_user
        If true, add exporter unix user and group
        [Default: True]
        type: bool

- apache_exporter_package
        Filename of the exporter package (without extension)
        [Default: (null)]
        type: str

- apache_exporter_package_dir
        Directory the exporter package is extracted to
        [Default: (null)]
        type: str

- apache_exporter_package_name
        Name of the exporter package
        [Default: (null)]
        type: str

- apache_exporter_package_url
        URL for the exporter package
        [Default: (null)]
        type: str

- apache_exporter_port
        Listen port
        [Default: 9117]
        type: int

- apache_exporter_register
        If true, register the exporter with the scrape servers
        [Default: True]
        type: bool

- apache_exporter_scrape_servers
        List of servers that scrape exporter metrics from the host,
        overrides prometheus_scrape_servers
        [Default: (null)]
        elements: str
        type: list

- apache_exporter_scrape_uri
        URI for the apache server status page, see
        https://httpd.apache.org/docs/2.4/mod/mod_status.html
        [Default: http://localhost/server-status?auto]

- apache_exporter_service
        Name of the exporter systemd service
        [Default: (null)]
        type: str

- apache_exporter_src_dir
        Directory for the exporter downloads
        [Default: (null)]
        type: str

- apache_exporter_tag
        Version git tag
        [Default: (null)]
        type: str

- apache_exporter_target
        Scrape target hostname and port
        [Default: (null)]
        type: str

- apache_exporter_user
        Name of the exporter unix user
        [Default: (null)]
        type: str

- apache_exporter_version
        Version to install (use "latest" for the latest version)
        [Default: latest]
        type: str

- apache_exporter_version_regex
        Regular expression for capturing the version from the latest
        tag
        [Default: (null)]
        type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter,main,wandansible.prometheus_exporter
    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter.apache,main,wandansible.prometheus_exporter.apache
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.prometheus_exporter
      src: https://github.com/wandansible/prometheus_exporter
    - name: wandansible.prometheus_exporter.apache
      src: https://github.com/wandansible/prometheus_exporter.apache

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: web_servers
      roles:
         - role: wandansible.prometheus_exporter.apache
           become: true
