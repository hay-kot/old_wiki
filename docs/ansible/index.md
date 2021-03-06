# Ansible

![Placeholder](/img/logos/ansible.png){: align=left style="height:15%;width:15%" }

Ansible is an open-source software provisioning, configuration management, and application-deployment tool enabling infrastructure as code. It runs on many Unix-like systems, and can configure both Unix-like systems as well as Microsoft Windows.

While the ansible code I use is currently not available. I'm working on documenting, cleaning up the code, and remove secrets so I can share it with the community. 

## Playbooks
Ansible Playbooks are the backbone of the services on my system. I've migrated from docker-compose to a system that fully automates deployments for all the services I need. Each service is relatively broken down into reusable chunks. Some exceptions should be noted like the peer_to_peer stack that is a collection of services bound together with a VPN. Each server has it's own playbook, and then those are all included in a `site.yml`  Additionally, there is an `update.yml` playbook for running updates on all servers.


- **local.yml** - Includes the main, secondary, matrix, and ansible playbooks
- **main.yml** - Used to set-up my main docker instances that houses most of my services
- **secondary.yml** - Used to set-up my secondary server that houses Pi-Hole and VPN
- **ansible.yml** - Used to setup the server that runs the ansible playbooks, when not ran from localhost
- **matrix.yml** - Used to update and secure the Matrix Chat server
- **update.yml** - Used to run updates across all machines
- **remote.yml** - Used to manage Caddy, Security, and Common configurations for VPS
