# Docker for Debian
Options:
  - install docker
  
1) Install from Github (git installed on your server)
```
ansible-galaxy install git+https://github.com/darexsu/ansible-role-docker.git
```
2) Example playbook
```
---
- hosts: all
  become: yes

  roles:
    - role: ansible-role-docker
      vars:
        docker_install: true
```
