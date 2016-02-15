# FAST capistrano cheatsheet/checklist
### Server side
* Add deployers group: `sudo groupadd deployers` 
* Add a user for deployments: `sudo usermod -a -G deployers deployer`
* Set proper permissions on your deploy folder: `sudo chown -R deployer:deployers /deploy/dir && sudo chmod -R g+w /deploy/dir`
* Configuration file
* cap deploy:setup

