1.启动数据库
将数据库文件映射到本地磁盘
docker run -itd -p 3306:3306   \
--restart always   \
--privileged=true   \
--name mysql   \
-e MYSQL_ROOT_PASSWORD=3nvisi0n!   \
-v /root/wordpress/mysql/data:/var/lib/mysql  \
mysql:5.7


2.启动wordpress
docker run -itd -p 8080:80  \
--restart always   \
--privileged=true   \
--name wordpress   \
-e WORDPRESS_DB_HOST=mysql   \
-e WORDPRESS_DB_PASSWORD=3nvisi0n! \
--link mysql \
wordpress
