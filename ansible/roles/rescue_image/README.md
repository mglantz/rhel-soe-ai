# rescue_image role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# Enable or disable rescue image
# NB. Rescue images will be created on next kernel install
rescue_image_enable: false

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# The rescue kernel is built once and is never updated by
# later kernel updates, so it stays bootable without
# security patches (requirements 6.3.3 and 2.2.4). When
# true, the role fails before making any change if
# rescue_image_enable is true. With rescue_image_enable
# false, existing rescue images are removed.
# NB. This role is not in the default configure_rhel_domains
# list, add rescue_image there for in-scope hosts.
rescue_image_pci_dss: false
</pre>

## License

GPLv3+
