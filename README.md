# config-nginx

Configure [nginx](http://nginx.com/) *sites* using [Ansible](http://www.ansible.com/).

We use this *ansible-playbook* to configure *multi-sites* servers serving different projects on different subdomains. The projects should be listed in `vars.yml`.
All listed projects get cloned and according nginx's *server* and *upstream* directives get written to a file, subsequently linked in `/sites-enabled/`. You just have to specify the repository URL and the network port used by your project.

To enable a specific **subdomain** go to the [DigitalOcean DNS dashboard](https://cloud.digitalocean.com/domains/) and register a new *A* record with the desired subdomain and the IP of the droplet.

This playbook is designed to work on droplets provisioned using the [nginx-nvm-mongo](https://github.com/wbkd/nginx-nvm-mongo) script.

### Requirements
- Python **2.7**

### Installation
Run:

	pip install ansible


### Usage
- Add the droplet IP to `hosts`
- Add your projects to `vars.yml`
- Run:

	ansible-playbook -i hosts nginx.yml

#### TODOs:
- [ ] Create DNS record for new subdomains
- [ ] Use DigitalOcean dynamic inventory
- [ ] Remove default site folder "/project"