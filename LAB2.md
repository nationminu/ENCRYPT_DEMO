openssl 을 사용한 공개키 실습(RSA)
=============

### 1. openssl을 사용하여 비공개키 생성

```openssl genrsa -out private.key 2048``` 

+ 2048 bit 길이를 가지는 키 private.key 파일을 생성

### 2. 비공개키를 이용하여 쌍이되는 공개키 생성

```openssl rsa -in private.key -out public.key -outform PEM -pubout```

+ private.key 라는 비공개키에 대한 공개키 public.key를 생성

### 3. 암호 문구를 password.txt 파일로 생성

```echo 'this is the my password' > password.txt```

### 4. 공개키(public.key)를 사용하여 password.txt 파일을 password.ssl 파일로 암호화

```openssl rsautl -encrypt -inkey public.key -pubin -in password.txt -out password.ssl```

+ password.txt 파일의 내용을 공개키(public.key)를 사용하여 RSA 방식으로 암호화하여 password.ssl 파일로 생성

### 5. 암호화된 파일의 내용 확인

```cat password.ssl```

### 6. 비공개키(private.key)를 사용하여 password.ssl 파일을 decryptpassword.txt 파일로 복호화

```openssl rsautl -decrypt -inkey private.key -in password.ssl -out decryptpassword.txt```

+ 공개키(public.key)로 암호화된 password.ssl 파일의 내용을 비공개키(private.key)로 복호화하여 decryptpassword.txt 파일로 생성.

### 7. 복호화된 파일의 내용 확인

```cat decryptpassword.txt```
