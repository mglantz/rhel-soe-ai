# files_acl role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of ACLs etc to apply to paths
# Uses ansible.posix.acl module
# Registers variable: acl_files
files_acl:
#  - path: /etc/foo.conf
#    entity: joe
#    etype: user
#    permissions: r
#    state: present

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before making any change if a
# requested ACL (state present) on a path under
# files_acl_pci_dss_log_paths would:
#  - grant write to anyone (10.3.2)
#  - grant read to etype other (10.3.1)
#  - grant read to a user or group not listed in
#    files_acl_pci_dss_log_readers (10.3.1)
files_acl_pci_dss: false
files_acl_pci_dss_log_paths:
  - /var/log
  - /run/log
files_acl_pci_dss_log_readers: []
</pre>

## License

GPLv3+
