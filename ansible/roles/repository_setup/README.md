# repository_setup role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of files to copy to /etc/yum.repos.d
repository_setup_repo_files_copy:
#  -

# List of files to remove in /etc/yum.repos.d
repository_setup_repo_files_remove:
#  -


# Do Red Hat Subscription Management configuration
# If false then rest of the parameters are ignored
repository_setup_rhsm_configure: true

# Subscribe or unsubscribe to Red Hat or Satellite
repository_setup_rhsm_subscribe: true

# Use new style curl URL to register. If set then
# the below RHSM parameters will be ignored. This
# assumes activation key in use. Must include all
# the curl arguments as a double-quoted string:
# "-ksS 'https://...' -H '...'"
repository_setup_rhsm_curl_args: ""

# Install Satellite katello-ca-consumer-latest.rpm
# This will use the rhsm_baseurl variable defined below
repository_setup_install_katello_rpm: true

# Force updating system facts at RHSM even if no
# changes made for subscription or repositories
repository_setup_rhsm_facts_update_always: false

# Configure subscription-manager to update package
# profile at RHSM after every dnf/yum transaction
repository_setup_package_profile_on_trans: true

# Red Hat Subscription Management parameters, see
# https://docs.ansible.com/ansible/latest/collections/community/general/redhat_subscription_module.html
# Leave activationkey and username undefined to skip RHSM configuration
repository_setup_rhsm_parameters:
  #activationkey:
  #org_id:

  #username:
  # This should come from vault
  #password:

  auto_attach: false
  #consumer_id:
  #consumer_name:
  #consumer_type:
  #environment:
  force_register: false
  #pool_ids:
  #  -
  #release:
  #rhsm_baseurl:
  #rhsm_repo_ca_cert:
  #server_hostname:
  #server_port:
  server_insecure: false
  #server_prefix:
  #server_proxy_hostname:
  #server_proxy_port:
  #server_proxy_user:
  #server_proxy_password:
  #server_proxy_scheme:
  #syspurpose:
  #  usage: Production
  #  role: Red Hat Enterprise Server
  #  service_level_agreement: Premium
  #  #addons: []
  #  sync: true
  #token:

# List of Red Hat / Satellite repository IDs to disable
repository_setup_rhsm_repositories_disable:
#  -

# List of Red Hat / Satellite repository IDs to enable
repository_setup_rhsm_repositories_enable:
#  - rhel-{{ ansible_facts.distribution_major_version }}-for-x86_64-baseos-rpms
#  - rhel-{{ ansible_facts.distribution_major_version }}-for-x86_64-appstream-rpms
#  - codeready-builder-for-rhel-{{ ansible_facts.distribution_major_version }}-x86_64-rpms

# Disable non-enabled Red Hat / Satellite repositories
repository_setup_rhsm_repositories_purge: true

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# Requirement 6.3.3 needs a working, trusted source of
# security patches. When true, the role fails before
# making any change if RHSM is configured and:
#  - repository_setup_rhsm_subscribe is false
#  - server_insecure is true
#  - repository_setup_rhsm_curl_args disables TLS
#    verification (-k or --insecure)
#  - the katello-ca-consumer RPM would be installed,
#    which skips GPG and TLS checks. Deploy the
#    Satellite CA with the certificates role and set
#    repository_setup_install_katello_rpm to false
# After all changes, the role fails if the host has no
# enabled repositories, or if any enabled repository has
# gpgcheck or sslverify turned off.
repository_setup_pci_dss: false
</pre>

## License

GPLv3+
