MySQL Server
============

This roles helps to install MySQL Server across RHEL and Ubuntu variants.
Apart from installing the MySQL Server, it applies basic hardening, like
securing the root account with password, and removing test databases. The role
can also be used to add databases to the MySQL server and create users in the
database. It also supports configuring the databases for replication--both
master and slave can be configured via this role.

Requirements
------------

This role requires Ansible 1.4 or higher, and platform requirements are listed
in the metadata file.

Role Variables
--------------

The variables that can be passed to this role and a brief description about
them are as follows:

      mysql_port: 3306                 # The port for mysql server to listen
      mysql_bind_address: "0.0.0.0"    # The bind address for mysql server
      mysql_root_db_pass: foobar       # The root DB password

      # A list that has all the databases to be
      # created and their replication status:
      mysql_db:                                 
           - name: foo
             replicate: yes
           - name: bar
             replicate: no

      # A list of the mysql users to be created
      # and their password and privileges:
      mysql_users:                              
           - name: benz
             pass: foobar
             priv: "*.*:ALL"

Examples
--------

1) Install MySQL Server and set the root password, but don't create any
database or users.

      - hosts: all
        roles:
        - {role: mysql, mysql_root_db_pass: foobar, mysql_db: none, mysql_users: none }

2) Sample playbook yaml if run as a task

	- name: Install and Configure mysql_fedora_ubuntu
	
	  hosts: all
	  
	  vars_files: 	  
		- defaults/main.yml

	  tasks: 
		- include: tasks/main.yml




Dependencies
------------

None

License
-------

BSD

Author Information
------------------

NagaLakshmi
 

