# FusionInventory

1. [Overview](#overview)
2. [Role Variables](#role-variables)
     * [Config Specific Variables](#config-specific-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
5. [Development](#development)
6. [License](#license)
7. [Author Information](#author-information)

## Overview

A role to manage FusionInventory agent installation and configuration.

## Role Variables

* **fusioninventory__agent_version** : The version of Fusioninventory agent to install [default : `2.6-1`].
* **fusioninventory__agent_depend_packages** : List of dependent packages to install.
* **fusioninventory__agent_recommend_packages** : List of recommended packages to install.
* **fusioninventory__agent_extra_packages** : List of extra packages to install (eg. to allow installation from a .deb file from Ansible).
* **fusioninventory__agent_package_url** : The URL used to download deb package for fusioninventory-agent [default : `"https://github.com/fusioninventory/fusioninventory-agent/releases/download/" + fusioninventory__agent_major_version + "/fusioninventory-agent_" + fusioninventory__agent_version + "_all.deb"` for Debian Stretch only].
* **fusioninventory__agent_deploy_state** : What is the desired state which this role should achieve [default : `present`].
* **fusioninventory__agent_service_name** : The service name to manage [default : `fusioninventory-agent`].
* **fusioninventory__agent_service_manage** : If the fusioninventory agent service should be managed [default : `true`].
* **fusioninventory__agent_conf_src** : Template used to provide agent configuration file [default : `../templates/etc/fusioninventory/agent.cfg.j2`].

### Config Specific Variables

Some variables used to generate FusionInventery agent.cfg file from Ansible template :

* **fusioninventory__agent_conf_server_url** : The URL of your Fusioninventory-server/GLPI/… [default⎵: ``].
* **fusioninventory__agent_conf_local_dir** : Write tasks results in a directory [default⎵: ``].
* **fusioninventory__agent_conf_no_task** : Do not run given task (separated by a comma) [default⎵: ``].
* **fusioninventory__agent_conf_tasks** : Run given tasks in given order (separated by a comma) [default⎵: ``].
* **fusioninventory__agent_conf_delaytime** : Set an initial delay before the first target [default⎵: `3600`].
* **fusioninventory__agent_conf_no_category** : Do not list given category items in inventory task (separated by a comma) [default⎵: ``].
* **fusioninventory__agent_conf_scan_homedirs** : Enable the scan of user home directories [default⎵: `false`].
* **fusioninventory__agent_conf_scan_profiles** : Enable the scan of users list [default⎵: `false`].
* **fusioninventory__agent_conf_no_ssl_check** : Disable check of the server SSL certificate [default⎵: `false`].
* **fusioninventory__agent_conf_no_httpd** : Disable embedded web server [default⎵: `true`].
* **fusioninventory__agent_conf_httpd_ip** : Interface/IP, the webserver server should listen to [default⎵: ``].
* **fusioninventory__agent_conf_httpd_port** : TCP port used by the webserver server to listen [default⎵: `62354`].
* **fusioninventory__agent_conf_httpd_trust** : hostname or IP or subnet authorized for http request [default⎵: ``].
* **fusioninventory__agent_conf_log_logger** : Specifies the logger backend to use [default⎵: `syslog`].
* **fusioninventory__agent_conf_log_facility** : Specifies the syslog facility to use for the syslog logger backend [default⎵: `LOG_DAEMON`].
* **fusioninventory__agent_conf_log_file** : Specifies the file to use for the file logger backend [default⎵: `/var/log/fusioninventory.log`].
* **fusioninventory__agent_conf_log_file_maxsize** : Specifies the maximum size for the log file, in MB [default⎵: `0`].
* **fusioninventory__agent_conf_log_color** : Enables color display for the stderr logger backend [default⎵: `false`].
* **fusioninventory__agent_conf_tag** : Add given tag to inventory results [default⎵: ``].
* **fusioninventory__agent_conf_debug** : If debug mode should be enabled [default⎵: `false`].

## Example Playbook

* Use defaults vars :

``` yaml
- hosts: mynode.DOMAIN
  roles:
    - role: ipr-cnrs.fusioninventory
      tags: ['role::fusioninventory', 'ipr', 'inventory']
```

* Install fusioninventory-agent from repository (unavailable in Debian Stretch and by default for all other release) :

``` yaml
- hosts: mynode.DOMAIN
  roles:
    - role: ipr-cnrs.fusioninventory
      fusioninventory__agent_package_url: ''
      tags: ['role::fusioninventory', 'ipr', inventory']
```

## Configuration

This role will :
* Install needed dependent packages of fusioninventory-agent.
* Once installed, the dependencies will not be removed.
* Install fusioninventory-agent package from official project package/URL.
* Generate agent's configuration file.
* Manage agent's systemd service.

## Development

This source code comes from our [Gogs instance][fusioninventory source] and the [Github repo][fusioninventory github] exist just to be able to send the role to Ansible Galaxy…

But feel free to send issue/PR here :)

Thanks to this [hook][gogs to github hook], Github automatically got updates from our [Gogs instance][fusioninventory source] :)

## License

[WTFPL][wtfpl website]

## Author Information

Jérémy Gardais
* Source : [on IPR's Gogs][fusioninventory source]
* [IPR][ipr website] (Institut de Physique de Rennes)

[gogs to github hook]: https://stackoverflow.com/a/21998477
[fusioninventory source]: https://git.ipr.univ-rennes1.fr/cellinfo/ansible.fusioninventory
[fusioninventory github]: https://github.com/ipr-cnrs/fusioninventory
[wtfpl website]: http://www.wtfpl.net/about/
[ipr website]: https://ipr.univ-rennes1.fr/
