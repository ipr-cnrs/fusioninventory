# FusionInventory

1. [Overview](#overview)
2. [Role Variables](#role-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
5. [Development](#development)
6. [License](#license)
7. [Author Information](#author-information)

## Overview

A role to manage FusionInventory agent installation and configuration.

## Role Variables

* **fusioninventory__agent_version** : The version of Fusioninventory agent to install [default : `2.4-2`].
* **fusioninventory__agent_depend_packages** : List of dependent packages to install.
* **fusioninventory__agent_package_url** : The URL used to download deb package for fusioninventory-agent [default : `http://debian.fusioninventory.org/downloads/fusioninventory-agent_{{ fusioninventory__agent_version }}_all.deb`].
* **fusioninventory__agent_deploy_state** : What is the desired state which this role should achieve [default : `present`].
* **fusioninventory__agent_service_name** : The service name to manage [default : `fusioninventory-agent`].
* **fusioninventory__agent_service_manage** : If the fusioninventory agent service should be managed [default : `True`].

## Example Playbook

* Use defaults vars :

``` yaml
- hosts: mynode.DOMAIN
  roles:
    - role: ipr-cnrs.fusioninventory
      tags: ['role::fusioninventory', 'ipr', inventory']
```

* Install fusioninventory-agent from repository (unavailable in Debian Stretch) :

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
* Install fusioninventory-agent package from official project package/URL.

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
