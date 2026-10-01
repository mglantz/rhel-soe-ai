# files_get role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of files to get over network
# Uses ansible.builtin.get_url module
# Registers variable: get_files
files_get:
#  - url: https://server.example.com/data.zip
#    url_username: admin
#    url_password: admin123
#    validate_certs: false
#    use_proxy: false
#    timeout: 5
#    dest: /var/tmp/data.zip
#    mode: '0600'

# Value for no_log parameter when getting
# files and using passwords, unset otherwise
files_get_no_log: true

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true, the role fails before downloading anything if an
# entry in files_get would:
#  - set validate_certs: false, accepting a certificate that
#    cannot be verified as trusted (4.2.1)
#  - send url_username/url_password over a URL that is not
#    https://, readable in transit (8.3.2)
# or if files_get_no_log is false while passwords are used,
# so credentials would be written to output and logs (8.3.2)
files_get_pci_dss: false
</pre>

## License

GPLv3+
