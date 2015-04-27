#puppet starting up
##precious links:
* [installing instructions](https://puppetlabs.com/misc/download-options)
* [debian install section](https://docs.puppetlabs.com/guides/install_puppet/install_debian_ubuntu.html)

* puppet is like knife in chef. puppet apply file.pp executes the list of resources contained in file. In puppet jargon, using puppet apply you ENFORCE the state described inside the pp file
* pp files are called manifests, and they are like cookbooks in opscode chef world
* with puppet resource you can execute directly a resource (that is like executing a block directly) , like f.e. `puppet resource user katie ensure ...`
* `ensure` automatically do the action against a resource if the check on the condition is false. 
* the manifests are compiled by puppet and built inside a CATALOG
* metaparameters are the things that you use in your resource to estabilish relations and other interdeps (*before*,*require*,*notify*,*subscribe*).
* variables are with a dollar sign, like $variable
* facter is the equivalent of chef ohai. And it obtains FACTS, that are like default system global vars ($ipaddress)
* modules are like cookbooks 
* modules name must have the same name of the direcory that contains them. Inside module dir you must have a manifests dir, and manifest shoul contain an init.pp manifest file 

##special notes:
* Avoid PC1 dpkg in debian, it installs a completely outdated version of puppet, despite the fact that the package is more recent
* check dns name resolution of the master and of the agents, could be messy to fix things after 
* test that hiera is working: `puppet apply -e '$somevar = hiera(foo) notify { $somevar: }'`
* test syntax of your yaml files: `ruby -e "require 'yaml'; YAML.load_file('hiera.yaml')"` 
* undef variable value is like a sort of NULL value


##other special notes

* In puppet.conf on each agent node, you can set the environment setting in either the agent or main config section. When that node requests a catalog from the Puppet master, it will request that environment. If you are using an ENC and it specifies an environment for that node, it will override whatever is in the config file
