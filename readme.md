# cloud-init demo with ansible-pull

Run the Demo with the following cloud-init code:
```
#cloud-config
package_update: true
package_upgrade: true
# if you're already installing other packages, you may
# wish to manually install ansible to avoid multiple calls
# to your package manager
packages:
  - git
  - ansible
ansible:
  install_method: pip
  pull:
    url: "github.com/hhansen06/cloud-init-demo.git"
    playbook_name: playbook-webserver.yml
```
