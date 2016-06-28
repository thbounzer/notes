## Vsftpd and virtual user configuration (debian)

### [Need passive mode configuration?](http://serverfault.com/questions/421161/how-to-configure-vsftpd-to-work-with-passive-mode)

```
pasv_enable=Yes
pasv_max_port=10100
pasv_min_port=10090
# Address might be needed:
pasv_address=xxx.xxx.xxx.xxx
```

### Configuration virtual users:

* `sudo apt-get install vsftpd libpam-pwdfile`

* vsftpd.conf:
```
guest_enable=YES
local_root=/srv/ftp/
# If you want to assign home to user by config file, then create a file named as the user name for each user inside the homedirconf, and assign home:
# local_root=/srv/ftp/homeforuser
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd/homedirconf
# Enable chroot, but remember to a-w on user's home 
chroot_local_user=YES
# If users need to upload files:
write_enable=YES
# Pam service name check
pam_service_name=vsftpd
```

### Virtual user root config:

Create a file that contains a string pointing to a local virtual root: `local_root=/home/local/root`

### Pam configuration:
```
#Remove debug once tested
auth required pam_pwdfile.so debug pwdfile=/path/to/passwdfile
account required pam_permit.so
```

### Passwd file generation:
* Format should be: `username:pwdhash`
* Generate hash: `openssl passwd -1`
