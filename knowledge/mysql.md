

# KILL掉系统里的MySQL进程；
    killall -9 mysqld 

# 用以下命令启动MySQL，以不检查权限的方式启动；
   mysqld --skip-grant-tables & 

# 然后用空密码方式使用root用户登录 MySQL；
   mysql -u root 

# 修改root用户的密码；
    MySQL> update mysql.user set password=PASSWORD('新密码') where User='root'; 
    MySQL> flush privileges; 
    MySQL> quit 

重新启动MySQL，就可以使用新密码登录了。

# mysql 命令
https://www.cnblogs.com/coder-wzr/p/8056415.html
