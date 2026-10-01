# accounts_local role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of local users to delete
# NB. Will remove users' home dirs
accounts_local_users_delete:
#  - testuser

# List of local groups to delete
accounts_local_groups_delete:
#  - testgroup

# List of local groups to create
# Uses ansible.builtin.group module
# Mandatory parameters: name, gid
accounts_local_groups_create:
#  - name: testgroup
#    gid: 12345

# List of local users to create
# Uses ansible.builtin.user module
# Mandatory parameters: name, uid
accounts_local_users_create:
#  - name: testuser
#    # This should come from vault
#    # Should be encrypted, see below
#    password: Foobar_12
#    uid: 12345
#    group: testgroup
#    comment: Test User
#    create_home: true
#    home: /home/testuser
#    shell: /bin/bash
#    expires: -1
#    password_expire_min: 7
#    password_expire_max: 365
#    #password_expire_warn: 14
#    # Allow or not unlimited sudo for user, this
#    # creates or removes /etc/sudoers.d/username
#    sudo_allow_all: false
#    # Require password or not for the above
#    sudo_passwordless: false
#    authorized_keys:
#      - ssh-ed25519 ... id_ed25519.pub
#    authorized_keys_exclusive: false

# Use true if providing crypted values,
# false to encrypt cleartext passwords.
accounts_local_password_encrypted: true
# Seed for password_hash salt value
accounts_local_password_salt_seed: "{{ inventory_hostname }}"

# Value for no_log parameter when setting passwords
# Recommended to use true and provide encrypted pws
accounts_local_no_log: true

# List of supplementary groups for users
# Mandatory parameters: name, groups, append
# Set append to false to make groups explicit
accounts_local_users_groups:
#  - name: testuser
#    groups:
#      - tcpdump
#      - wheel
#    append: false

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before making any change if
# the requested users/groups conflict with Requirement 8:
#  - users with a managed password must set
#    password_expire_max between 1 and
#    accounts_local_pci_dss_password_max_days (8.3.9)
#  - non_unique UIDs/GIDs are not allowed (8.2.1)
#  - sudo_allow_all with sudo_passwordless is not
#    allowed (8.2.2, 8.3.1)
#  - with accounts_local_password_encrypted, password
#    hashes must be SHA-512 or yescrypt (8.3.2)
#  - without accounts_local_password_encrypted, cleartext
#    passwords must be at least
#    accounts_local_pci_dss_password_min_length characters
#    and contain letters and digits (8.3.6); these are
#    hashed in-role and so bypass pam_pwquality
accounts_local_pci_dss: false
accounts_local_pci_dss_password_max_days: 90
accounts_local_pci_dss_password_min_length: 12
</pre>

## License

GPLv3+
