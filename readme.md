# cloud-init demo with ansible-pull
## Example #1: Install Webserver (apache2) and add hostname to index.html
Run the Demo with the following cloud-init code:
```
#cloud-config
package_update: true
package_upgrade: false
users:
  - default
  - name: kim
    passwd: "$6$kW4vfBM9kGgq4hr$TFtHW7.3jOECR9UCBuw9NrdSMJETzSVoNQGcVv2y.RqRUzWDEtYhYRkGvIpB6ml1fh/fZEVIgKbSXI9L1B6xF."
    shell: /bin/bash
    lock-passwd: false
    ssh_pwauth: True
    chpasswd: { expire: False }
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
packages:
  - git
  - ansible
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
runcmd:
 - [ sh, -c, echo "========= cloud-init-demo -- rancher =========" ]
 - ansible-pull -U https://github.com/hhansen06/cloud-init-demo -d /opt/org/repo playbook-rancher.yml
```
