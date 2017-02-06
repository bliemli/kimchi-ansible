kimchi-ansible
==============

Ansible role for installing and configuring Kimchi.


Requirements
------------

This role requires Ansible 2.2 or higher and platform requirements are listed in the metadata file.

Role Variables
--------------

	# Enable PCI passthrough (default: false)
	enable_pci_passthrough: true

	# Wok configuration
	wok:
	  # Hostname or IP address
	  host: 0.0.0.0
	  # Admin interface HTTP port
	  port: 8000
	  # Admin interface HTTPS port
	  ssl_port: 8001
	  # Whether to only listen on HTTPS or both
	  https_only: false
	  # CherryPy port
	  cherrypy_port: 8010
	  # Websocket proxy port
	  websockets_port: 64667
	  # Session timeout in minutes
	  session_timeout: 10
	  # Full path to an SSL certificate in PEM format (leave empty for self-signed cert)
	  ssl_cert: 
	  # Full path to the private key in PEM format
	  ssl_key: 
	  # The server's running environment
	  environment: production
	  # Max request body size in KB
	  max_body_size: 4 * 1024 * 1024
	  # Log directory (if changed needs manual change of logrotate config)
	  log_dir: /var/log/wok
	  # Log level (debug, info, warning, error or critical)
	  log_level: info
	  # Authentication method (pam, ldap)
	  method: pam
	  # LDAP server (only if auth method is ldap)
	  ldap_server: 
	  # LDAP search base
	  ldap_search_base: "ou=People, dc=wok, dc=org"
	  # LDAP search filter
	  ldap_search_filter: "uid=%(username)s"
	  # User IDs regarded as Wok admins (comma-separated string)
	  ldap_admin_id: "foo@foo.com, bar@bar.com"

Examples
========

	- hosts: kimchi
	  become: true
	  vars:
	    enable_pci_passthrough: true
	    wok:
	      session_timeout: 30

Dependencies
------------

None

License
-------

MIT

Author Information
------------------

Benjamin Affolter

