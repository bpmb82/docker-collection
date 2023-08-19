# docker-install
-------------

Ansible role to deploy Docker on Debian or CentOS based hosts. This repo is meant to be used as a Git submodule.

## Requirements
------------

 - Server running Ubuntu 20/22 or CentOS 7 or higher

## Use as Git submodule

Needs to be in a 'roles' folder:
```
/roles/docker-install/$CONTENTS_OF_REPO
/playbook.yml
```

Usage:
```
cd roles/
git submodule add git@bitbucket.org:vislink-engineering/docker-install.git
```

## Role Variables
-------------

`swarm_mode`

Optional, determines whether to install Docker Swarm mode (default = `true`)
*We default to swarm mode because it allows us to use Docker Secrets*

`single_host`

Optional, determines if we need to install on a single host or multiple (default = `true`)

`advertise_address`

Optional, address to bind the docker swarm to

`primary_master`

Optional, host to use as the primary swarm master

## Example Playbook
-------------

```
- hosts: servers
  roles:
    role:
      - docker-install
        vars:
          - advertise_address: 192.168.1.100
```