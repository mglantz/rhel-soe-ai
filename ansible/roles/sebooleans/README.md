# sebooleans role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of SELinux booleans to disable
# Uses ansible.posix.seboolean module
sebooleans_disable:
#  - nis_enabled

# List of SELinux booleans to enable
# Uses ansible.posix.seboolean module
sebooleans_enable:
#  - kerberos_enabled

# Skip missing SELinux boolean instead of
# failing when trying to configure them
sebooleans_skip_missing: true

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before making any change if:
#  - sebooleans_enable contains a boolean from
#    sebooleans_pci_dss_denied that has no documented
#    business justification in
#    sebooleans_pci_dss_exceptions (2.2.4, 2.2.5, 2.2.6)
# and a boolean that is not known on the host fails
# the role regardless of sebooleans_skip_missing, so a
# documented setting is never silently skipped (2.2.1)
sebooleans_pci_dss: false

# Booleans that weaken memory protections or allow
# anonymous write / privileged remote logins
sebooleans_pci_dss_denied:
  - cluster_use_execmem
  - ftpd_anon_write
  - httpd_execmem
  - mmap_low_allowed
  - selinuxuser_execheap
  - ssh_sysadm_login
  - tftp_anon_write
  - unconfined_dyntrans_all
  - xserver_execmem

# Business justification per denied boolean, 2.2.5
# Must be a non-empty string to permit enabling it
sebooleans_pci_dss_exceptions: {}
#  httpd_execmem: "CHG0012345: vendor JIT runtime, WAF in front"
</pre>

## License

GPLv3+
