# Create Users with Ansible Vault Integration

## Task

Write an Ansible playbook to securely create a local system user by leveraging an encrypted variable file. **Do not include module code or playbook syntax—only outline the task in detail.**

### Detailed Steps

1. **Prepare a Plain-Text Variable File**

   * Create a YAML file at `vars/user_vars.yml`.
   * Define two keys:

     * `username`: the name of the user account to create (e.g., `demouser`).
     * `password`: the user’s password in plain text (e.g., `SuperSecretP@ss`).

2. **Encrypt the Variable File**

   * Use Ansible Vault to encrypt `vars/user_vars.yml`.

     * Choose either:

       * **Create**: `ansible-vault create vars/user_vars.yml` to write and encrypt in one step.
       * **Encrypt**: `ansible-vault encrypt vars/user_vars.yml` if the file already exists.
   * Ensure the resulting file remains named `vars/user_vars.yml`, but is in encrypted format.

3. **Reference the Encrypted Variables in Your Playbook**

   * In your playbook (`create_user_secure.yml`), include the encrypted file under `vars_files`:

     ```yaml
     vars_files:
       - vars/user_vars.yml
     ```
   * This tells Ansible to load `username` and `password` securely from the Vault.

4. **Define the User-Creation Task**

   * Use the Ansible `user` module to:

     * Create or update the account named by `username`.
     * Assign the account’s password using the `password` variable (hashed as required by the module).
   * Do **not** write out actual module parameters here—students will implement this section themselves.

5. **Execute the Playbook with Vault Credentials**

   * Run the playbook and prompt for the Vault password at runtime:

     ```bash
     ansible-playbook create_user_secure.yml --ask-vault-pass
     ```
   * Alternatively, use a Vault password file:

     ```bash
     ansible-playbook create_user_secure.yml --vault-password-file ~/.vault_pass.txt
     ```
