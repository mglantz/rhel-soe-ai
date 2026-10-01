# security_hardening role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# Verify Secure Boot
# Fails if UEFI Secure Boot is not enabled
secure_boot_verify: false

# Verify FIPS enabled
# Fails if FIPS mode is not enabled
fips_mode_verify: false

# One of: disabled, integrity, confidentiality
# NB. Enabling lockdown will prevent using kdump
# NB. Supported RHEL versions: RHEL 9+
kernel_lockdown: disabled

# SELinux state
# Allowed values: enforcing, permissive, disabled
selinux: enforcing

# System-wide crypto policy
# NB. FIPS mode must be enabled during installation
crypto_policy: DEFAULT

# Enable or disable SCP protocol (not scp(1))
scp_protocol_enable: true

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before making any change if:
#  - selinux is not enforcing (2.2.6)
#  - crypto_policy, or any of its subpolicies, is listed
#    in security_hardening_pci_dss_crypto_denied, as
#    these allow insecure algorithms, key sizes or
#    protocol fallback (2.2.7, 4.2.1, 8.3.2)
security_hardening_pci_dss: false

# Crypto policies and subpolicies not permitted on
# in-scope systems (case-insensitive)
security_hardening_pci_dss_crypto_denied:
  - LEGACY
  - SHA1
  - AD-SUPPORT-LEGACY
</pre>

## License

GPLv3+
