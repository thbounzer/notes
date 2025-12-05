## New hetzner setup notes/todo

* Assume latest Debian minimal distro;
* Ansible playbook with configuration to setup:
  * Install minmal utils:
    [vim, htop, sudo, libvirt, qemu, shorewall(maybe), openvpn ]
  * My user account, pubkeys/sudo
  * My SSHD config
  * Configures libvirt/qemu
  * Configures openvpn - (maybe wireguard simpler)
* Once libvirt in place/can run, then provision infra with Terraform: 
  * Coredns vm
  * Haproxy vm
  * Thalos nodes
  * Kamal nodes
* Static sites and simple stateless apps can go to kamal (I want to keep using it to have a test bench)
* All other more involved apps, run on K8S
* Once K8S infra is in place
  * Terraform/Helm to provision services
