mapr-tcollector
=========

Install a fork of tcollector which includes MapR metrics support.

Requirements
------------

tcollector uses OpenTSDB to store metrics, so you should have OpenTSDB running somewhere. If you're using this repo for tcollector, you might as well also use this one for opentsdb: https://github.com/vicenteg/mapr-opentsdb

Role Variables
--------------

You need to set the following:

`mapr_webserver`: This is a node in your MapR cluster that runs `webserver`. The collector hits this for metrics via REST.

`mapr_webserver_port`: Usually 8443.

`mapr_username`: Make sure this user has `login` permissions. That's all it needs.

`mapr_password`: It's the password.

`tsdb_host`: The hostname for the machine running opentsdb.

Dependencies
------------

Example Playbook
----------------

	- hosts: vagrant
	  roles:
	    - { role: mapr-tcollector,
		tsdb_host: "localhost",
		mapr_webserver: "localhost",
		mapr_webserver_port: 8443,
		mapr_username: "mapr",
		mapr_password: "mapr" }

License
-------

MIT

Author Information
------------------

vgonzalez at mapr dot com
