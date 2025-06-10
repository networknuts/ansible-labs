## Playbook: Deploy HTTPD Webserver with Variables

### Description
Write an Ansible playbook that uses variables to deploy and configure the Apache HTTPD webserver on your target hosts. The playbook must be idempotent and ensure the webserver is installed, running, and accessible, with all key values driven by variables.

### Requirements
- **Filename**: `deploy_httpd.yml`
- **Hosts**: `webservers`
- **Privilege escalation**: `become: yes`
- **Modules to use**:
  - `ansible.builtin.yum` (or `ansible.builtin.package`)
  - `ansible.builtin.service`
  - `ansible.builtin.copy`
  - `ansible.posix.firewalld`

### Variables
Define the following variables (either in a `vars:` section at the top of your playbook or in a separate `vars/main.yml`):

```yaml
httpd_package: httpd
httpd_service: httpd
index_path: /var/www/html/index.html
index_content: |
  <html>
    <head><title>Welcome</title></head>
    <body><h1>Welcome to your HTTPD server!</h1></body>
  </html>
firewalld_service: http
```

### Tasks

1. **Install HTTPD**

2. **Use the package module with name: "{{ httpd_package }}" to install HTTPD.**

3. **Start and Enable HTTPD**

4. **Use the service module with name: "{{ httpd_service }}" to ensure it is started and enabled at boot.**

5. **Create index.html**

6. **Use ansible.builtin.copy to write index_content to index_path.**

7. **Allow HTTP in Firewalld**

8. **Use the firewalld module to add firewalld_service to firewalld_zone permanently and reload firewalld.**

