#puppet starting up
##precious links:
* [installing instructions](https://puppetlabs.com/misc/download-options)
* [debian install section](https://docs.puppetlabs.com/guides/install_puppet/install_debian_ubuntu.html)

* puppet is like knife in chef. puppet apply file.pp executes the list of resources contained in file. In puppet jargon, using puppet apply you ENFORCE the state described inside the pp file
* pp files are called manifests, and they are like recipes in opscode chef world
* with puppet resource you can execute directly a resource (that is like executing a block directly) , like f.e. `puppet resource user katie ensure ...`
* `ensure` automatically do the action against a resource if the check on the condition is false. 
* the manifests are compiled by puppet and built inside a CATALOG
 
