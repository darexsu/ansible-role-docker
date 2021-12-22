# ansible role docker

install from galaxy
```
ansible-galaxy install darexsu.docker
```
Example playbook
```
---
- hosts: myservers
  become: yes

  roles:
    - role: darexsu.docker
      vars:
        docker_install: true
```
Install from Github (git installed on your server)
```
ansible-galaxy install git+https://github.com/darexsu/ansible-role-docker.git
```
Example playbook
```
---
- hosts: myservers
  become: yes

  roles:
    - role: ansible-role-docker
      vars:
        docker_install: true
```
