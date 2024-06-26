# Ansible Role OpenSearch Dashboards

This roll installs opensearch-dashboards
It is a modified fork of the [official opensearch ansible role](https://github.com/opensearch-project/ansible-playbook).
Checkout the CHANGELOG.txt for all changes.

**Please note that this modified version is not meant for production use!**
### Prerequisite

- **Ansible 2.9+**
- **Java 8**

# Configuration

```
  # Start service after installation and run tests
  os_test: True

  os_version: "2.13.0"
  os_dashboards_version: "2.13.0"
  os_dashboards_user: opensearch-dashboards
  os_download_url: https://artifacts.opensearch.org/releases/bundle/opensearch
  os_user: opensearch
  os_cluster_name: os-cluster
  admin_password: "myStrongPassword@123!"
  kibanaserver_password: "Test@6789"
  logstash_password: "Test@456"
  domain_name: aecid-testbed.local
  opensearch_hostname: search.aecid-testbed.local
  opensearch_hosts:
          search.aecid-testbed.local:
            ip: 192.168.100.11
```

# Example playbook

```yaml
- name: Deploy opensearch
  hosts: opensearch
  remote_user: ubuntu
  become: true
  vars:
    os_version: "2.13.0"
    os_dashboards_version: "2.13.0"
    os_dashboards_user: opensearch-dashboards
    os_download_url: https://artifacts.opensearch.org/releases/bundle/opensearch
    os_user: opensearch
    os_cluster_name: os-cluster
    admin_password: "myStrongPassword@123!"
    kibanaserver_password: "Test@6789"
    logstash_password: "Test@456"
    domain_name: aecid-testbed.local
    opensearch_hostname: search.aecid-testbed.local
    opensearch_hosts:
            search.aecid-testbed.local:
              ip: 192.168.100.11
  roles:
    - role: hostname
      vars:
        hostname: search
        hostname_ip: 192.168.100.11
        hostname_fqdn: search.aecid-testbed.local
    - role: dashboards
```


## License

This project is licensed under the [Apache v2.0 License](LICENSE.txt).

## Copyright

Copyright OpenSearch Contributors. See [NOTICE](NOTICE.txt) for details.
