## Playbook: Deploy HTTPD Webserver

### Description
Write an Ansible playbook to deploy and configure the Apache HTTPD webserver on your target hosts. The playbook must be idempotent and ensure the webserver is installed, running, and accessible.

### Requirements
- **Filename**: `deploy_httpd.yml`
- **Hosts**: `webservers`
- **Privilege escalation**: `become: yes`
- **Modules to use**:
  - `ansible.builtin.yum` (or `ansible.builtin.package`) for package installation
  - `ansible.builtin.service` for service management
  - `ansible.builtin.copy` for file creation
  - `ansible.posix.firewalld` for firewall configuration

### Tasks
1. **Install HTTPD**  
   Use the package module to install the `httpd` package.

2. **Start and Enable HTTPD**  
   Use the service module to ensure the `httpd` service is started and enabled on boot.

3. **Create `index.html`**  
   Use `ansible.builtin.copy` to place a simple HTML file at `/var/www/html/index.html`.  
   - Content example:  
     ```html
     <html>
       <head><title>Welcome</title></head>
       <body><h1>Welcome to your HTTPD server!</h1></body>
     </html>
     ```

4. **Allow HTTP in Firewalld**  
   Use the firewalld module to:
   - Add the `http` service to the public zone permanently
   - Reload firewalld to apply changes

### Idempotency
Running this playbook multiple times should make no changes if the system is already configured as described.
