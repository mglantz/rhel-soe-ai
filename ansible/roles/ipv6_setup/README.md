# ipv6_setup role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# Enable or disable IPv6 using sysctl settings
# Boot parameter to disable IPv6 will be removed
# See https://access.redhat.com/solutions/8709
ipv6_setup_enable: true

# Some applications (e.g., Samba) require IPv6 stack
# to be enabled to function but need no IPv6 routing
# This option keeps IPv6 on for the loopback device
# This option has effect only when disabling IPv6
ipv6_setup_loopback_persist: false

# Set to true to configure NetworkManager/IPv6 with this role
# When using system_roles.network to configure NM set to false
ipv6_setup_configure_nm: true

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before making any change if
# IPv6 is enabled without being documented as necessary:
# only necessary protocols may be enabled (2.2.4). Either
# set ipv6_setup_enable: false or, when IPv6 is required,
# set ipv6_setup_pci_dss_ipv6_required: true and record the
# business need in the system configuration standard
ipv6_setup_pci_dss: false
ipv6_setup_pci_dss_ipv6_required: false
</pre>

## License

GPLv3+
