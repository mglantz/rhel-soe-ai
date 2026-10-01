# cron_setup role

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)

Please see the collection main page for a higher level description.

## Configuration

Below are the role default values from defaults/main.yml:

<pre>
---
# List of crontab entries to update
# Uses ansible.builtin.cron module
cron_setup_entries:
#  - name: LC_ALL
#    env: true
#    job: C.UTF-8
#  - name: refresh tokens
#    job: /usr/local/bin/refresh-tokens
#    special_time: daily
#  - name: obsoleted task
#    state: absent

# List of allowed crontab users in cron.allow
# When set to null cron.allow will be removed
cron_setup_allow_file: []

# List of denied crontab users in cron.deny
# When set to null cron.deny will be removed
cron_setup_deny_file: null

# PCI DSS 4.0.1 guardrails, see docs/POLICY.md and
# docs/PCI-DSS-v4_0_1.md. Enable only for in-scope systems.
# When true:
#  - the role fails before making any change unless
#    cron_setup_allow_file is a list, so cron use is
#    deny all unless a user is listed (7.2.1, 7.3.3)
#  - the role fails before making any change if an entry
#    in cron_setup_entries puts a job in the crontab of a
#    user other than root who is not in
#    cron_setup_allow_file (7.2.2)
#  - /etc/crontab is set to 0600 and /etc/cron.d and
#    /etc/cron.{hourly,daily,weekly,monthly} to 0700,
#    owned by root (2.2.6, 7.2.1)
#  - after applying, the role lists all user crontabs
#    and /etc/cron.d files as evidence for access reviews
#    (7.2.4, 7.2.5.1), and fails if a user other than root
#    who is not in cron_setup_allow_file has a crontab
cron_setup_pci_dss: false
</pre>

## License

GPLv3+
