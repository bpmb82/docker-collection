# docker-collection
Collection of docker images deployed with Ansible

Services currently supported:

* traefik
* sabnzbd
* sonarr
* radarr
* bazarr
* emby
* jellyfin
* home assistant
* wg-easy
* slskd

## How to

1. Install ansible, see: [Ansible install](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible-with-pip)
2. Open env.yml.example and adjust as needed (explanations of all vars is in the example file)
3. Save the file as env.yml
4. Run the deploy.yml playbook with ansible-playbook:
```ansible-playbook deploy.yml```

Every service will use the following DNS records:

```$SERVICE.example.com```

So, will result in sabnzbd.example.com, sonarr.example.com etc etc.

## NOTES

### OS

I have and will only test this on Linux, it might work on WSL as well but this has not been tested. This playbook will also install Docker
but only if the detected OS is debian or redhat based.

### DNS

You will obviously have to create the correct DNS records for all these services.

### Firewall

You might still need to adjust your firewall to allow specific traffic.

## Plans

### Add docker swarm compatibility (now experimental)

The biggest problem here was that I need USB devices attached to Home Assistant and docker swarm doesn't support this.
I've tried attaching it to the overlay networks but for some reason I've yet to figure out, I couldn't get that to work.