openssl 을 사용한 공개키 실습
=============

### 1. openssl을 사용하여 비공개키 생성

```openssl genrsa -out private.key 2048``` 

### 2. 비공개키를 이용하여 쌍이되는 공개키 생성

```openssl rsa -in private.key -out public.key -outform PEM -pubout```

+ **enc -e -des3 :** des3 방식으로 암호화
+ **-in plainpassword.txt -out encryptpassword.bin :** plainpassword.txt 파일을 encryptpassword.bin 로 암호화하여 저장.

### 3. 암호 문구를 password.txt 파일로 생성

```echo 'this is the my password' > password.txt```

### 4. 공개키(public.key)를 사용하여 password.txt 파일을 password.ssl 파일로 암호화

```openssl rsautl -encrypt -inkey public.key -pubin -in password.txt -out password.ssl```

+ **enc -d -des3 :** des3 방식으로 복화화
+ **-in encryptpassword.bin -out decryptpassword.txt :** encryptpassword.bin 파일을 decryptpassword.txt 로 복호화하여 저장.

### 5. 암호화된 파일의 내용 확인

```cat password.ssl```

### 6. 비공개키(private.key)를 사용하여 password.ssl 파일을 decryptpassword.txt 파일로 복호화

```openssl rsautl -decrypt -inkey private.key -in password.ssl -out decryptpassword.txt```

### 7. 복호화된 파일의 내용 확인

```cat decryptpassword.txt```
