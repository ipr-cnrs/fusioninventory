## v1.1.2

* Add missing dependencies (libyaml-tiny-perl, libxml-treepp-perl and ucf).
* The role also works on Debian Buster.

## v1.1.1

### Fix

* Moved back fusioninventory__agent_package_url definition in default configuration
even if it's Debian related to allow installation of a newer version than one
available in repos or installation from private repository (for Stretch).

## v1.1.0

### Features

* Add RHEL7 support (thanks @roumano).

## v1.0.3

### Fix
* Fix Manage trust requests without authentication token (#1)

## v1.0.2

### Fix
* Fix E405 Remote package tasks should have a retry.
* Fix E602 Don't compare to empty string.
* Set empty dependencies line to fix Galaxy warning.

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
