# ansible role docker

1) install from galaxy
```
ansible-galaxy install darexsu.docker
```
2) Example playbook
```
---
- hosts: myservers
  become: yes

  roles:
    - role: darexsu.docker
      vars:
        docker_install: true
```
1) Install from Github (git installed on your server)
```
ansible-galaxy install git+https://github.com/darexsu/ansible-role-docker.git
```
2) Example playbook
```
---
- hosts: myservers
  become: yes

  roles:
    - role: ansible-role-docker
      vars:
        docker_install: true
```
