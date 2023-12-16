# cloud-init demo with ansible-pull

Run the Demo with the following cloud-init code:
```
#cloud-config
package_update: true
package_upgrade: false

packages:
  - git
ansible:
  install_method: pip
  pull:
    url: "github.com/hhansen06/cloud-init-demo.git"
    playbook_name: playbook-webserver.yml
```
