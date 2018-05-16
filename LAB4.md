Tomcat 을 이용한 쇼핑몰(jpetstore) 설치
=============

### 1. java 설치
```
sudo apt-get install openjdk-8-jdk

java -version
```

### 2. tomcat 설치
```
git clone https://github.com/nationminu/tomcat_petstore.git
cd ./tomcat_petstore/apache-tomcat-8.5.31/bin/
./startup.sh
ps -ef|grep tomcat
```
+ github.com 에 구성된 tomcat 다운로드후 Tomcat 실행

### 3. 웹서버 연동
```
sudo a2enmod proxy
sudo a2enmod proxy_http 

sudo vi /etc/apache2/apache.conf

ProxyPass /petstore http://127.0.0.1:8080/petstore
ProxyPassReverse /petstore http://127.0.0.1:8080/petstore

sudo /etc/init.d/apache2 restart
```

+ Apache 웹서버에서 지원하는 proxy 모듈로 Tomcat 과 연동

### 4. 웹브라우저로 쇼핑몰 확인
```
http://localhost/petstore
```
