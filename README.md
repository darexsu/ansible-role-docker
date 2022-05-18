# Ansible role Docker

[![CI Molecule](https://github.com/darexsu/ansible-role-docker/actions/workflows/ci.yml/badge.svg)](https://github.com/darexsu/ansible-role-docker/actions/workflows/ci.yml)&emsp;![](https://img.shields.io/static/v1?label=idempotence&message=ok&color=success)&emsp;![Ansible Role](https://img.shields.io/ansible/role/d/59232?color=blue&label=downloads)

  - Role:
      - [platforms](#platforms)
      - [install](#install)
      - [merge behaviour](#merge-behaviour)
  - Playbooks (merge version):
      - [install and configure: Docker](#install-and-configure-docker-merge-version)
        - [install: Docker, repo: distribution](#install-docker-repo-distribution-merge-version)
        - [install: Docker, repo: third_party](#install-docker-repo-third_party-merge-version)
        - [configure: add users to docker group](#configure-add-users-to-docker-group-merge-version)
  - Playbooks (full version):
      - [install and configure: Docker](#install-and-configure-docker-full-version)
        - [install: Docker, repo: distribution](#install-docker-repo-distribution-merge-version)
        - [install: Docker, repo: third_party](#install-docker-repo-third_party-merge-version)
        - [configure: add users to docker group](#configure-add-users-to-docker-group-full-version)

### Platforms

|  Testing         |  Docker            |
| :--------------: | :----------------: |
| Debian 11        |:heavy_check_mark:  |
| Debian 10        |:heavy_check_mark:  |
| Ubuntu 20.04     |:heavy_check_mark:  |
| Ubuntu 18.04     |:heavy_check_mark:  |
| Oracle Linux 8   |:heavy_check_mark:  |
| Rocky Linux 8    |:heavy_check_mark:  |  

### Install
```
ansible-galaxy install darexsu.docker --force
```

### Merge behaviour

Replace or Merge dictionaries (with "hash_behaviour=replace" in ansible.cfg):
```
# Replace             # Merge
---                   ---
  vars:                 vars:
    dict:                 merge:
      a: "value"            dict: 
      b: "value"              a: "value" 
                              b: "value"

# How does merge work?
Your vars [host_vars]  -->  default vars [current role] --> default vars [include role]
  
  dict:          dict:              dict:
    a: "1" -->     a: "1"    -->      a: "1"
                   b: "2"    -->      b: "2"
                                      c: "3"
    
```
##### Install and configure: Docker (merge version)
```yaml
---
- hosts: all
  become: true

  vars:
    merge:
      # Docker
      docker:
        enabled: true

      # Docker -> install
      docker_install:
        enabled: true

      # Docker -> config
      docker_config:
        enabled: true
        docker_users: ["{{ ansible_user}}"]

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
##### Install: Docker, repo: distribution (merge version)
```yaml
---
- hosts: all
  become: true

  vars:
    merge:
      # Docker
      docker:
        enabled: true
        repo: "distribution"

      # Docker -> install
      docker_install:
        enabled: true

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
##### Install: Docker, repo: third_party (merge version)
```yaml
---
- hosts: all
  become: true

  vars:
    merge:
      # Docker
      docker:
        enabled: true
        repo: "third_party"

      # Docker -> install
      docker_install:
        enabled: true

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
##### Configure: add users to docker group (merge version)
```yaml
---
- hosts: all
  become: true

  vars:
    merge:
      # Docker
      docker:
        enabled: true

      # Docker -> config
      docker_config:
        enabled: true
        docker_users: ["{{ ansible_user}}"]

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
##### Install and configure: Docker (full version)
```yaml
---
- hosts: all
  become: true

  vars:
    # Docker
    docker:
      enabled: true
      repo: "third_party"
      service:
        enabled: true
        state: "started"

    # Docker -> install
    docker_install:
      enabled: true

    # Docker -> config
    docker_config:
      enabled: true
      docker_users: ["{{ ansible_user}}"]

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
##### Install: Docker, repo: distribution (full version)
```yaml
---
- hosts: all
  become: true

  vars:
    # Docker
    docker:
      enabled: true
      repo: "distribution"
      service:
        enabled: true
        state: "started"

    # Docker -> install
    docker_install:
      enabled: true

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
##### Install: Docker, repo: third_party (full version)
```yaml
---
- hosts: all
  become: true

  vars:
    # Docker
    docker:
      enabled: true
      repo: "third_party"
      service:
        enabled: true
        state: "started"

    # Docker -> install
    docker_install:
      enabled: true

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
##### Configure: add users to docker group (full version)
```yaml
---
- hosts: all
  become: true

  vars:    
    # Docker
    docker:
      enabled: true
      repo: "third_party"
      service:
        enabled: true
        state: "started"

    # Docker -> config
    docker_config:
      enabled: true
      docker_users: ["{{ ansible_user}}"]

  tasks:
    - name: role darexsu docker
      include_role:
        name: darexsu.docker
```
