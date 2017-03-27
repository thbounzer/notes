# Some notes related on centos

* Networking
    * Interfaces configurations is inside /etc/sysconfig/network-scripts/ file looks like ifcfg-eth0
    * Static conf example:
        *  `DEVICE=eth1
            HWADDR=08:00:27:27:5F:9D
            TYPE=Ethernet
            ONBOOT=yes
            NM_CONTROLLED=yes
            BOOTPROTO=static
            IPADDR=192.168.56.222
            NETMASK=255.255.255.0`
    * DHCP example: 
        *  `DEVICE=eth0
            HWADDR=08:00:27:65:CD:CC
            TYPE=Ethernet
            UUID=a5a9528b-4148-495d-92f9-b5000181f4c6
            ONBOOT=yes
            NM_CONTROLLED=yes
            BOOTPROTO=dhcp`
    * Iptables is enabled by default with ssh enabled as well.
        * Configuration can be found in /etc/sysconfig/iptables
    * hostname can be changed from /etc/sysconfig/network

* Yum (packages)
    * Proxy conf:
        * Edit /etc/yum.conf with following settings: 
             `proxy=http://proxyaddress:proxyport
              # The account details for yum connections
              proxy_username=username
              proxy_password=password`

