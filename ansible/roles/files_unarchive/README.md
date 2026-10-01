# files_unarchive role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of files to unarchive
# Uses ansible.builtin.unarchive module
# Registers variable: unarchive_files
files_unarchive:
#  - src: /tmp/installer.zip
#    dest: /opt/acme
#    remote_src: true

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before making any change if an
# entry in files_unarchive would:
#  - extract to a dest under files_unarchive_pci_dss_log_paths,
#    overwriting audit logs (10.3.2)
#  - set a world-writable mode on extracted files (2.2.6, 10.3.2)
#  - set validate_certs: false, accepting a certificate that
#    cannot be verified as trusted (4.2.1)
files_unarchive_pci_dss: false
files_unarchive_pci_dss_log_paths:
  - /var/log
  - /run/log
</pre>

## License

GPLv3+
