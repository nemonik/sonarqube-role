# SonarQube Ansible role

![Basic role syntax check](https://github.com/nemonik/sonarqube-role/workflows/Basic%20role%20syntax%20check/badge.svg)

An Ansible role for ensuring the configuration of [SonarQube](https://www.sonarqube.org/).

## Requirements

Requires Kubernetes, MetalLb and private Docker Registry installed.

## Role Variables

| Variable                   | Required | Default         | Choices       | Comments                                         |
|----------------------------|----------|-----------------|---------------|--------------------------------------------------|
| docker_timeout             | yes      | 300             | Integer value | Number of seconds before docker pull timeout     |
| docker_retries             | yes      | 60              | Integer value | Number of tries for docker pull                  |
| docker_delay               | yes      | 10              | Integer value | Delay in seconds between pull retries            |
| default_retries            | yes      | 60              | Integer value | Default number of retries                        |
| default_delay              | yes      | 60              | Integer value | Default delay in seconds between retries         |
| gitlab_host                | no       | not defined     | IP address    | If define will integrate authentication with     |
| gitlab_port                | no       | not defined     | Integer value | If defined will integrate authentication with    |
| vault_gitlab_root_password | no       | not defined     | String value  | Needed for integration with GitLab               |
| sonarqube_version          | yes      | 8.3.1-community | version       | Docker image tag                                 |
| sonarqube_host             | yes      | 192.168.0.205   | ip address    | IP address                                       |
| sonarqube_port             | yes      | 9000            | Integer value | The port to listen on                            |
| images_cache_path          | no       | not defined     | Path          | Path to folder used to cache saved Docker images |

## Example Playbook

An example can be found used in my Hands-on DevOps course's [ansible/master-playbook.yml](https://github.com/nemonik/hands-on-DevOps/blob/master/ansible/master-playbook.yml).

```
- hosts: masters
  remote_user: vagrant
  roles:
    - k3s-server
    - docker-registry
    - metallb
    - gitlab
    - sonarqube
```

The above Ansible playbook uses my [K3s-server role](https://github.com/nemonik/k3s-server-role) to install Lightweight Kubernetes (K3s), my [metallb role](https://github.com/nemonik/metallb-role) to install MetalLB and my [Docker Registry role](https://github.com/nemonik/docker-registry-role) to install a private Docker registry.

For more information and to see this role put into action checkout my [Hands-on DevOps class](https://github.com/nemonik/hands-on-DevOps) project.

## License

3-Clause BSD License

## Author Information

Michael Joseph Walsh <mjwalsh@nemonik.com>
