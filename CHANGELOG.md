## v1.X.Y

### Fix
* Switch to Github URL to download deb file (thanks to @roumano - PR #16).
* Pipe ansible_managed to `comment` jinja filter to manage multi-lines.

## v1.4.1

### Fix
* truthy warnings with ansible-lint.
* complete rhel8 support (thanks @mjourdan − PR #13).

## v1.4.0

### Add
* Manage new parameters:
  * **tag** with fusioninventory__agent_conf_tag variable
  * **no-task** with fusioninventory__agent_conf_no_task variable
  * **tasks** with fusioninventory__agent_conf_tasks variable
  * **logger** with fusioninventory__agent_conf_log_logger variable
  * **logfacility** with fusioninventory__agent_conf_log_facility variable
  * **logfile** with fusioninventory__agent_conf_log_file variable
  * **logfile-maxsize** with fusioninventory__agent_conf_log_file_maxsize variable
  * **color** with fusioninventory__agent_conf_log_color variable

## v1.3.1

### Fix

* Update package list for Debian from `dpkg --info` of the last 2.6 version (fix #11).

### Enhancement

* Flatten packages list to allow condition.
* Split fusioninventory__agent_depend_packages content to 3 variables (for Debian)
  * fusioninventory__agent_depend_packages
  * fusioninventory__agent_recommend_packages
  * fusioninventory__agent_extra_packages
* Manage dependencies only when FI is installed from a downloaded package.

## v1.3.0

### Fix

* Add role_name info in meta.
* Set a default mode (0644) in ini_file.
* with_first_found fail when ansible_distribution vars file is missing (#5).

### Enhancement

* Update dependencies for .deb package.

## v1.2.1

### Fix

* Warnings with yamllint.

## v1.2.0

### Features

* Add RHEL8 support (thanks @mjourdan) (#7).
* The role also works on Debian Bullseye.

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
