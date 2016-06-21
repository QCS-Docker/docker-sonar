# docker-sonar

### 在MySQL中运行
#### 1.启动MySQL
```sh
docker run --name some-mysql \
           -e MYSQL_USER=sonar \
           -e MYSQL_PASSWORD=sonar \
           -e MYSQL_DATABASE=sonar \
           -e MYSQL_ROOT_PASSWORD=verysecret \
           -d slsay/docker-mysql
```
#### 2. 运行sonar
```sh
   docker run --name some-sonarqube \
           -p 9000:9000 -p 9092:9092 \
           -e SONARQUBE_JDBC_USERNAME=sonar \
           -e SONARQUBE_JDBC_PASSWORD=sonar \
           -e SONARQUBE_JDBC_URL=jdbc:mysql://mysql:3306/sonar?useUnicode=true\&characterEncoding=utf8\&rewriteBatchedStatements=true  \
           --link some-mysql:mysql \
           -d slsay/docker-sonar
```

### 访问sonar
```sh
docker-machine ip
```
http://MACHINE_VM_IP:9000/  
登录账号： admin/admin
