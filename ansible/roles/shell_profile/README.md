# shell_profile role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# Shell profile template to use
shell_profile_file:

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, a read-only shell idle timeout of
# shell_profile_pci_dss_tmout seconds is deployed for
# sh-family (TMOUT) and csh-family (autologout) shells
# so idle sessions are logged out (8.2.8). It is loaded
# after shell_profile_file, so that cannot override it.
# When false, the timeout files are removed again.
shell_profile_pci_dss: false
# Idle timeout in seconds, 60 to 900 (15 minutes)
shell_profile_pci_dss_tmout: 900
</pre>

## License

GPLv3+
