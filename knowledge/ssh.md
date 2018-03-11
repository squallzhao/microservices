
#ssh支持pem

      将密钥上传至Linux服务器，并修改权限。以文件king.pem为例:

      chmod 600 king.pem

      修改密钥格式为OpenSSH，如果询问，留空回车：

      ssh-keygen -p -f king.pem

      生成公钥.pub文件：

      ssh-keygen -e -f king.pem >> king.pem.pub

      下载生成.pub文件，在使用SecrueCRT连接时指定相应pub文件即可。
