---
{"dg-publish":true,"permalink":"/linux/ansible-role-to-install-github-runners-on-local-computer/","tags":["public","ansible","Github"],"noteIcon":"1","created":"2023-10-03T14:26:41.602+02:00","updated":"2024-02-23T14:29:13.000+01:00"}
---

This uses this role; [GitHub - macunha1/ansible-github-actions-runner: Idempotent Ansible role that installs and configures self-hosted GitHub Actions Runners (yeah, plural!)](https://github.com/macunha1/ansible-github-actions-runner/tree/master)

Example of implementation below

```yaml
---

- name: Add the user 'ghrunner' with a specific uid and a primary group of 'root'

hosts: Server14

tasks:

- name: create runner user

ansible.builtin.user:

name: ghrunner

comment: github runner

group: sudo

  

#install github runner

- hosts: Server14

become: yes

become_user: root

roles:

- role: macunha1.github_actions_runner

vars:

gh_runner_config_labels:

- linux

- Server14

- self-hosted

gh_runner_service_user: ghrunner

gh_runner_config_url: https://github.com/ORG/REPO
#Add token here on run time!

gh_runner_config_token:

gh_runner_installation_path: /home/ghrunner/usr/local/share/github-actions-runner

gh_runner_workspace_path: /home/ghrunner/var/cache/github-actions-runner

gh_runner_config_labels: ["self-hosted","linux","Server14"]
```
