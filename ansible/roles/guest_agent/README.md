# guest_agent role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# Install or remove server VM guest agents
# This role will detect and enable correct
# agent and remove other agents if present
# Will uninstall all agents if set to false
# NB. Only agents from RHEL repositories
#     are considered for un/installation
#     Currently recognized platforms are:
#       - Azure
#       - KVM/QEMU
#       - Nutanix AHV
#       - VMware
guest_agent_enable: true

# Remove unneeded firmware packages on VMs
# VMs with device passthrough may need these
guest_agent_remove_firmware: true

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, hypervisor-to-guest functions that run commands,
# transfer files, or change credentials outside the guest's
# own access control and logging are disabled (2.2.4, 8.2):
#  - KVM: the RPCs below are removed from the qemu-ga allow
#    list, or added to its block list, in /etc/sysconfig/qemu-ga
#  - VMware: guest operations (run program, file transfer)
#    are disabled in /etc/vmware-tools/tools.conf
# Azure/Hyper-V waagent extensions are not changed
guest_agent_pci_dss: false
guest_agent_pci_dss_qemu_blocked_rpcs:
  - guest-exec
  - guest-exec-status
  - guest-file-close
  - guest-file-flush
  - guest-file-open
  - guest-file-read
  - guest-file-seek
  - guest-file-write
  - guest-set-user-password
  - guest-ssh-add-authorized-keys
  - guest-ssh-get-authorized-keys
  - guest-ssh-remove-authorized-keys
</pre>

## License

GPLv3+
