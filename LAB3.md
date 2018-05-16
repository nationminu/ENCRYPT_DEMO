Apache 웹서버 설치 (Debian)
=============

### 1. Apache 웹서버 설치
```
sudo apt-get install apache2
```

### 2. SSL 모듈 활성화
```
sudo a2enmod ssl
```

### 3. Apache 웹서버 기동
```
sudo /etc/init.d/apache2 start
```

### 4. 개인키 및 사설 인증서 생성
```
sudo mkdir /etc/apache2/ssl
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt


Generating a 2048 bit RSA private key
.......+++
......................+++
writing new private key to '/etc/apache2/ssl/apache.key'
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:KR
State or Province Name (full name) [Some-State]:Seoul
Locality Name (eg, city) []:Seoul City
Organization Name (eg, company) [Internet Widgits Pty Ltd]:semyung
Organizational Unit Name (eg, section) []:semyung
Common Name (e.g. server FQDN or YOUR name) []:www.semyung.com
Email Address []:test@localhost
```

### 5. Apache 웹서버 SSL 설정
```
sudo vi /etc/apache2/sites-available/default-ssl.conf 

<IfModule mod_ssl.c>
    <VirtualHost _default_:443>
        ServerAdmin admin@example.com
        ServerName your_domain.com
        ServerAlias www.your_domain.com
        DocumentRoot /var/www/html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.crt
        SSLCertificateKeyFile /etc/apache2/ssl/apache.key
        ....
    </VirtualHost>
</IfModule>

sudo a2ensite default-ssl.conf
```

### 6. Apache 웹서버 재기동
```
sudo /etc/init.d/apache2 restart
```
