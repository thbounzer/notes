# Libvirt virtual machines

* Listing network domains: `virsh net-list --all`
* Starting network domain: `virsh net-start netname`
* Converting images (Only supported format for snapshots is qcow2, maybe you need to convert between formats): `qemu-img convert -f src_fmt -O dst_fmt srcimg.fmt dstimg.fmt`
* Making snapshots: `virsh snapshot-create-as machinename snapshotname "snapshot description"
* Reverting to snapshots: `virsh snapshot-revert --domain machinename snapshotname`
