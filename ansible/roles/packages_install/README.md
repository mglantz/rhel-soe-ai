# packages_install role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
packages_install:
  - acl
  - bash-completion
  - bind-utils
  - curl
  - dnf-plugins-core
  #-git-core
  - man-pages
  #- mokutil
  #- mlocate
  - nano
  - openssh-clients
  #- perl-interpreter
  - psmisc
  - python3
  - python3-libselinux
  - policycoreutils-python-utils
  #- rsync
  #- sos
  - tar
  #- tmux
  #- unzip
  #- vim-enhanced
  #- wget
  - xz
  - zstd

# List of dnf excludes
packages_install_exclude:
#  - emacs

# Enable or disable dnf module 'install_weak_deps' parameter
packages_install_weak_deps: true

# Display results on output
packages_install_display_results: false

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before installing anything if
# packages_install contains a package that provides an
# insecure (cleartext) service, protocol or daemon listed in
# packages_install_pci_dss_insecure (2.2.4, 2.2.5, 2.2.7).
# Set packages_install_pci_dss_insecure_justified to true
# only after the business justification and additional
# security features are documented (2.2.5).
packages_install_pci_dss: false
packages_install_pci_dss_insecure_justified: false
packages_install_pci_dss_insecure:
  - ftp
  - rsh
  - rsh-server
  - talk
  - talk-server
  - telnet
  - telnet-server
  - tftp
  - tftp-server
  - vsftpd
  - xinetd
  - ypbind
  - ypserv
</pre>

## License

GPLv3+
