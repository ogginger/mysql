Executable bash scripts that setup a mysql server or client.

bin/mysqld - [-f](optional) [password](optional)
  1. If no arguments are given, the script tries to deploy a mysql server using etc/mysql/passwd as the root password, and var/lib/mysql as the data store.
    -If either of those already exist a console message is printed instead.
  2. If a password is supplied then the script will try to create the directories var/lib/mysql and etc/mysql, write the given password to etc/mysql/passwd, and then deploy the server.
    -If either etc/mysql/passwd exists or var/lib/mysql contains data then a console message is printed instead.
  3. If -f is supplied with a password, then the script will remove etc/mysql/passwd and var/lib/mysql/, create new instances of those files and directories, and then deploy the server.
    -If no password is supplied then a console message is printed instead.
  4. The container maps the ports 3306:3306 so that remote clients can connect to the mysql server via the host.
  
bin/mysql - (No Arguments)
  1. The mysql client connects to the prexisting and running mysql server deployed with bin/mysqld.
    -The client has to wait until the server is done initializing before making a successful connection.
    
