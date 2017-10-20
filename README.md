# OpenResty Ansible Role
This role installs OpenResty from the official ppa and links /etc/openresty and openresty service files to the nginx equivalents. On systems managed by systemd, it installs an nginx service for openresty.


## Testing
`vagrant up` will start an ubuntu trusty and ubuntu xenial virtualbox instance and run this role against them.
