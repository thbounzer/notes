#Setup tests with chef-solo, Vagrant and Capistrano
---
1. Setup chef 
 * Now there is [chef-dk](http://downloads.chef.io/chef-dk/).
 * Verify chef-dk installation with ´chef-verify´
 * chef-dk uses an embedded environment for the related gems, ruby, and so on. To avoid conflicts, run ´chef exec, chef gem´ This is a must (IMHO) if you have rvm installed. 
 * Create kitchen base working directory structure ´kitchen init --create-gemfile´
 * Edit .kitchen.yml according to your needs
 * Check virtualbox running machines: ´VBoxManage list runningvms´
 * You can setup chef client on the guest running ´kitchen setup machinename´, default provisioner is chef-solo
 * Destroy (if needed) machine instances with `kitchen destroy machinename`

2. Cookbooks
 * Generate cookbook, using chef-dk: ´chef generate cookbook nameofcookbook´


A. Various things to keep in mind
 * *Ohai*: Is a chef provided tool, runs on a node and creates a json with an abundant set of informations related to the node machine.
 * *Modes*: local-mode, client-mode, solo. Solo will be deprecated in the feature, get used to more powerful local-mode.
 * *Knife and Chef*: Future chef-dk releases will unify all operations related to cookbook management to use just the chef command instead of knife. chef generate command supports -for example- creation of cookbooks in incremental way.  
