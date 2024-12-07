Ansible Role: What's up Docker?
===============================

Install What's up Docker Docker Compose project.

- https://getwud.github.io/wud/
- https://github.com/getwud/wud

Requirements
------------

Requires the following to be installed:
- docker
- docker compose

Role Variables
--------------

Common system variables:

```yaml
timezone: UTC
```

Common Docker projects variables:

```yaml
# Base directory for Docker projects
docker_projects_path: # /var/apps
```

Available role variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Docker project variables

whatsupdocker_project_name: whatsupdocker

# Docker project dynamic vars (uses `docker_project_name` prefix, adapt if overriden)

# Traefik options
whatsupdocker_traefik_loadbalancer_server_port: 3000
whatsupdocker_traefik_entrypoints: http,https
whatsupdocker_traefik_middlewares:
  - "internal-access@file"


# What's up Docker project variables

# Docker image version
whatsupdocker_version: latest

# Local watcher scheduling
whatsupdocker_watcher_local_cron: '0 */2 * * *'
```

Dependencies
------------

This role depends on :
- [djuuu.docker_project](https://github.com/Djuuu/ansible-role-docker-project)

Some variables allow integration with:
- [djuuu.traefik_docker](https://github.com/Djuuu/ansible-role-traefik-docker)

Example Playbook
----------------

```yaml
- hosts: all
  gather_facts: true
  gather_subset:
    - "!all"
    - "!min"
    - user_id

  roles:
    - djuuu.whatsupdocker
```

License
-------

Beerware License
