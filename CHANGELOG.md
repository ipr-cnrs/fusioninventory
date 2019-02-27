## v1.0.2

### Fix
* Fix E405 Remote package tasks should have a retry.

## v1.0.1

### Features
* Package URL is defined only for Debian Stretch.

## v1.0.0

### Features
* Install dependent packages for fusioninventory-agent.
* Don't remove dependent packages.
* Install fusioninventory-agent package from URL or repos.
* If desired, remove fusioninventory-agent package.
* Generate agent's configuration file.
* Restart agent's service if needed.
* Ensure to install xz-utils to allow ansible to install a debian package manually.
