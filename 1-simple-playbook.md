## Playbook: Create User

### Description
Write an Ansible playbook to create a local system user on target hosts. The playbook must be idempotent and ensure the user exists with the specified properties.

### Requirements
- **Filename**: `create_user.yml`
- **Module**: `user`

### Task
- Use the `user` module to:
  1. Ensure a user named `demouser` exists.
  2. Set the UID to `1001`.
  3. Assign the user to the `wheel` group.
  4. Use `/bin/bash` as the login shell.
  5. Provide an appropriate comment (GECOS) such as `"Demo User Account"`.
  6. Be idempotent (running the playbook again makes no changes if the user already exists correctly).

---

## Playbook: Delete User

### Description
Write an Ansible playbook to remove a local system user from target hosts. The playbook must be idempotent and ensure the user does not exist.

### Requirements
- **Filename**: `delete_user.yml`
- **Module**: `user`

### Task
- Use the `user` module to:
  1. Ensure the user named `demouser` is absent.
  2. Remove the home directory and mail spool.
  3. Be idempotent (running the playbook again makes no changes if the user is already absent).
