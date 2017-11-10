# A systemd cheatsheet
* `systemctl`: display status of all services (SysV/LSB/systemd native) services
* `ps xawf -eo pid,user,cgroup,args` or `systemd-cgls`: Show process tree with cgroups

* How systemd [use init](http://unix.stackexchange.com/questions/233468/how-does-systemd-use-etc-init-d-scripts)? 

### Reduce excessive verbosity:
* edit /etc/systemd/system.conf, uncomment LogLevel and make it: LogLevel=notice. Then `systemctl restart rsyslog`, and `systemd-analyze set-log-level notice`
