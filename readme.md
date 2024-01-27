# cloud-init demo with ansible-pull
## Example #1: Install Webserver (apache2) and add hostname to index.html
Run the Demo with the following cloud-init code:
```
#cloud-config
package_update: true
package_upgrade: false

packages:
  - git
  - ansible
  - htop
runcmd:
 - [ sh, -c, echo "========= cloud-init-demo -- webserver =========" ]
 - ansible-pull -U https://github.com/hhansen06/cloud-init-demo -d /opt/org/repo playbook-webserver.yml
```

## Example #2: Install Rancher Server in Docker
Run the Demo with the following cloud-init code:
```
#cloud-config
package_update: true
package_upgrade: false

packages:
  - git
  - ansible
  - htop
runcmd:
 - [ sh, -c, echo "========= cloud-init-demo -- rancher =========" ]
 - ansible-pull -U https://github.com/hhansen06/cloud-init-demo -d /opt/org/repo playbook-rancher.yml
```
