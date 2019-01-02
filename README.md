# check_package_center
Synology packages update check for Nagios

The connexion is made to the NAS using the webapi. The required username and password are those to login to DSM with the rights to access Package Center application.

Command usage:  
		"check_package_center.php [-h -v] -H hostname [-P port] [-s] -u username -p password  
		"
		"List of options
		"    -H : hostname to be checked
		"    -P : port to connect to. Defaut is 5000 or 5001 if -s if set
		"    -u : username to connect to host
		"    -p : password to connect to host
		"    -s : activate https (http by default)
		"    -v : verbose. Activate debug info
		"    -h : print this help.

				
Usage example in Nagios config:  
define command {  
	command_name check_package_center  
	command_line /path/to/libexec/check_package_center.php -H $HOSTADDRESS$ -u $ARG1$ -p $ARG2$  
}


define service {  
	host	my.host  
	service_description Package Center Status  
	check_command check_package_center!username!password  
	use generic-service  
}