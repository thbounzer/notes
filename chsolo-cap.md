#Setup tests with chef-solo, Vagrant and Capistrano
---
1. Setup chef 
 * Now there is [chef-dk](http://downloads.chef.io/chef-dk/).
 * Verify chef-dk installation with ´chef-verify´
 * chef-dk uses an embedded environment for the related gems, ruby, and so on. To avoid conflicts, run ´chef exec, chef gem´ This is a must (IMHO) if you have rvm installed. 
 * Create kitchen base working directory structure ´kitchen init --create-gemfile´
 * Edit .kitchen.yml according to your needs
