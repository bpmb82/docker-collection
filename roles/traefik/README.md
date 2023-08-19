# traefik-swarm
-------------

Ansible role to deploy Traefik to docker swarm, can be used for general web-based proxies but also specifically for Linkmatrix and Management. This repo is meant to be used as a Git submodule.

## Requirements
------------

 - Running docker swarm
 - Azure DNS credentials (when using letsencrypt which is default)

## Use as Git submodule

Needs to be in a 'roles' folder:
```
/roles/traefik-swarm/$CONTENTS_OF_REPO
/playbook.yml
```

Usage:
```
cd roles/
git submodule add git@bitbucket.org:vislink-engineering/traefik-swarm.git
```

## Role Variables
-------------

`application`

Required, will be used to specify which docker network to use. For Linkmatrix, you could simply set it to 'linkmatrix'

`letsencrypt`

Defaults to `true`, uses Azure DNS challenge and will prompt for secrets

`loadbalancer`

Required when used behind a loadbalancer, default is `false`

`linkmatrix`

Optional, when set it will also open up port 1883 for MQTT, defaults to `false`

`management`

Optional, when set it will also open up port 8847 for WMT Management, defaults to `false`

`debug`

Optional, will set Traefik logs to debug, defaults to `false`

## Example Playbook
-------------

```
- hosts: servers
  roles:
    role:
      - traefik-swarm
        vars:
          - linkmatrix: true
```