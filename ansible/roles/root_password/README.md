# root_password role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# Use true if providing crypted value,
# false to encrypt cleartext password.
root_password_encrypted: true

# Seed for password_hash salt value
root_password_salt_seed: "{{ inventory_hostname }}"

# This should come from vault
#root_password:

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before changing the password if
# root_password conflicts with Requirement 8:
#  - with root_password_encrypted, the hash must be
#    SHA-512 or yescrypt, or a locked value (8.3.2)
#  - without root_password_encrypted, the cleartext must
#    be at least root_password_pci_dss_min_length long and
#    contain both letters and digits (8.3.6)
# Rotating the vault value at least every 90 days (8.3.9)
# and using a unique value per host (8.3.5) are not
# checked here and remain the vault owner's responsibility.
root_password_pci_dss: false
root_password_pci_dss_min_length: 12
</pre>

## License

GPLv3+
