# service_state role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of services/units to mask
# Registers variable: mask_services
service_state_mask:
#  - dnf-makecache.timer

# List of services/units to unmask
# Registers variable: unmask_services
service_state_unmask:
#  - httpd.service

# List of services/units to disable and stop
# Registers variables: {disable,stop}_services
service_state_disable:
#  - mlocate-updatedb.timer
#  - nfs-client.target
#  - rpcbind.service
#  - rpcbind.socket

# List of services/units to enable and start
# Registers variables: {enable,start}_services
service_state_enable:
#  - irqbalance.service

# List of services to reload/restart
# Default is to restart, use state to reload
# Optionally can require given service state
# or status to carry out or not the operation
# Registers variables: {reload,restart}_services
service_state_restart:
#  - pmcd.service
#  - name: haproxy.service
#    state: reloaded
#    require: running

# Skip missing services/units instead of
# failing when trying to enable/start them
service_state_skip_missing: false

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, service_state_pci_dss_units (insecure,
# cleartext services) are disabled and stopped in addition
# to service_state_disable (2.2.4, 2.2.5, 2.2.7), and the
# role fails before changing anything if one of them is
# listed in service_state_enable or service_state_unmask
# without being listed in service_state_pci_dss_justified.
# Pairs with packages_remove_pci_dss, which removes the
# packages providing these units.
service_state_pci_dss: false
service_state_pci_dss_units:
  - ntalk.socket
  - rexec.socket
  - rlogin.socket
  - rsh.socket
  - telnet.socket
  - tftp.service
  - tftp.socket
  - vsftpd.service
  - xinetd.service
  - ypbind.service
  - ypserv.service

# Units from the list above to leave alone on in-scope
# systems. Only list a unit here once its business
# justification and additional security features are
# documented (2.2.5).
service_state_pci_dss_justified: []
</pre>

## License

GPLv3+
