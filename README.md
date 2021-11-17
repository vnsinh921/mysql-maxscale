
Role infomation
--------------

- Role install maxscale HA mysql

Role Variables
--------------

	# Node read only
	sql_read_only_servers: 
  	  - name: slave1  
    	address: 127.0.0.1  
    	port: 3306  

	# Node read write  
	sql_read_write_servers:  
  	  - name: master1  
      address: 127.0.0.1  
      port: 3306  

	# Grant maxscale user privilege  
		CREATE USER 'maxscaleuser'@'%' IDENTIFIED BY '0atvL0nqgmFVHpD3';  
		GRANT SELECT ON mysql.user TO 'maxscaleuser'@'%';  
		GRANT SELECT ON mysql.db TO 'maxscaleuser'@'%';  
		GRANT SELECT ON mysql.tables_priv TO 'maxscaleuser'@'%';  
		GRANT SELECT ON mysql.* TO 'maxscaleuser'@'%';  
		GRANT SHOW DATABASES ON *.* TO 'maxscaleuser'@'%';  
		GRANT REPLICATION CLIENT on *.* to 'maxscaleuser'@'%';  
		FLUSH PRIVILEGES;  
	


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - {role: mysql-maxscale, tags: mysql-maxscale}



