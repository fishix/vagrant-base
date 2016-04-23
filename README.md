1. Setup IP address for vagrant in vagrant file
	grep -nrs 'VAGRANT_IP_ADDRESS' .
2. Setup vhost
	grep -nrs 'VHOST_NAME' .
3. Create symfony project and setup path in config files
	grep -nrs 'SYMFONY_DIRECTORY' .
4. Setup database configs
	grep -nrs 'SYMFONY_DATABASE' .
5. Add vhost to /etc/hosts
6. Create vagrant machine
	vagrant up
