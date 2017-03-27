# Setup tests with chef-solo, Vagrant and Capistrano
---
1. **Setup chef** 
 * Now there is [chef-dk](http://downloads.chef.io/chef-dk/).
 * Verify chef-dk installation with `chef-verify`
 * chef-dk uses an embedded environment for the related gems, ruby, and so on. To avoid conflicts, run `chef exec, chef gem` This is a must (IMHO) if you have rvm installed. 
 * Create kitchen base working directory structure `kitchen init --create-gemfile`
 * Edit .kitchen.yml according to your needs
 * Check virtualbox running machines: `VBoxManage list runningvms`
 * You can setup chef client on the guest running `kitchen setup machinename`, default provisioner is chef-solo
 * Destroy (if needed) machine instances with `kitchen destroy machinename`

2. **Cookbook**
 * Generate cookbook, using chef-dk: `chef generate cookbook nameofcookbook`
 * Generate a file for a cookbook: `chef generate file nameofthefile`
 * Deploy the created cookbook (converging a node): `kitchen converge machinename` (machine name is needed if you have multiple guest host configured in the kitchen)
 * Generate a template: `chef generate template nameoftemplate`   
 * Generate a attribute file: `chef generate attribute nameofattribute`
 * Attribute priorities (from highest to lowest): Auto(Ohai attr) --> Recipe defined attrs --> Attribute file defined attrs  

3. **Knife**
 * Use **knife** to download and add cookbook, upload cookbook on the chef server and talk with it
 * Knife uses apache solr for searching, queries must be built using solr syntax
 * 


A. **Various things to keep in mind**
 * *Guest test machine settings*: particular settings (for example network customization) must be passed within kitchen.yml file, under [driver section](https://github.com/test-kitchen/kitchen-vagrant#-network)
 * *Ohai*: Is a chef provided tool, runs on a node and creates a json with an abundant set of informations related to the node machine.
 * *Modes*: local-mode, client-mode, solo. Solo will be deprecated in the feature, get used to more powerful local-mode.
 * *Knife and Chef*: Future chef-dk releases will unify all operations related to cookbook management to use just the chef command instead of knife. chef generate command supports -for example- creation of cookbooks in incremental way.
 * *to converge* means to deploy a cookbook
 * *debugging attributes*: Use `pp node.debug_value(attribute_name)`  to print priorities set for the attribute.  
 * *Kitchen test* is slow. Huge improvement if someone implements caching of files downloaded from the web.  
