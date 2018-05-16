HTTP 와 HTTPS 의 Packet 분석
=============

### 1. tcpdump 를 사용하여 http 포트 패킷 캡처
```
sudo tcpdump port 80 -w http.log
```

### 2. tcpdump 를 사용하여 https 포트 패킷 캡처
```
sudo tcpdump port 443 -w https.log
```

### 3. 웹 브라우저를 사용하여 http/https 로그인
```
http://localhost/pestore
```

### 4. 패킷 파일 확인
```
strings http.log
strings https.log

cat http.log | grep j2ee
cat https.log | grep j2ee
```

+ 패킷 파일 내용 중 로그인시 사용한 아이디 패스워드가 검색되는지 확인
