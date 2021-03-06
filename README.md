Semaphor Ansible role
=====================

Installs the [Semaphor] encrypted chat client for Linux.

Requirements
------------

Debian-based OS. (Semaphor packages exist for RHEL derivatives
as well, but aren't automated as part of this role).

Role Variables
--------------

```yaml
# Required dependencies during deb package installation.
semaphor_apt_packages:
  - gconf-service
  - gconf2
  - git
  - gvfs-bin
  - libxtst6
  - xdg-utils

# This URL will automatically pull down whatever the latest deb package is,
# but doesn't seem to support requesting a specific version.
semaphor_deb_package_url: "https://spideroak.com/releases/semaphor/debian"

# This version number will need to be manually bumped as new releases are
# issued. Haven't found a decent API yet for reliably determing the most
# recent version available and using that.
semaphor_version: "1.2.1"

# Hard-coded as from v1.2.1; the Semaphor project does not use GPG signatures
# for verification (yet), so SHA256 checksum over TLS is the best we've got.
semaphor_deb_package_sha256: d6fbd2497b4d0368d4c804b16aa9631bb05de2d3be966fa0f17d87bb7caaff3a

semaphor_deb_package_filename: "{{ 'semaphor_'+semaphor_version+'_amd64.deb' }}"
semaphor_download_directory: /usr/local/src
```

Example Playbook
----------------

    - hosts: workstations
      roles:
         - role: freedomofpress.semaphor

License
-------

MIT

[Semaphor]: https://spideroak.com/solutions/semaphor
