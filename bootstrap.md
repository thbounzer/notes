#Fast puppet master/agent configuration setup (Debian)

* Official [install instructions](https://puppetlabs.com/misc/download-options)
* [Debian install section](https://docs.puppetlabs.com/guides/install_puppet/install_debian_ubuntu.html)

##Master setup:

* Download the correct dpkg (follow the updated official guide)
* Check that the FQDN of the machine is the one that you want
* Install puppetmaster with passenger : sudo apt-get install puppetmaster-passenger
* Master is up. Check if passenger is running correctly

##Agent setup:

* Install the agent: sudo apt-get install puppet
* Set the puppet master server directive inside the puppet.conf file (/etc/puppet.conf), adding in the main section `server = yourmaster.yourdomain.yourtld`
* if you want to enable the agent at boot, edit /etc/default/puppet and set START to YES
* Execute `sudo puppet agent --test`. Now the agent will query the master asking for configuration info. The agent is still not signed by the master, it will recognize this and it will ask for a signing request.
* Go on your master, exec `sudo puppet cert list`, if everything is working, you should  see the signing request of your agent
* Sign the agent with `sudo puppet cert sign youragent.yourdomain.yourtld` 

Basic master/agent configuration is now inplace.
