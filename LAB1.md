openssl 을 사용한 대칭키 실습
=============

1. 암호 문구를 plainpassword.txt 파일로 생성

```echo 'this is the my password' > plainpassword.txt ``` 

2. openssl 을 사용하여 plainpassword.txt 파일을 encryptpassword.bin 파일로 암호화

```openssl enc -e -des3 -in plainpassword.txt -out encryptpassword.bin```

+ enc -e -des3 : des3 방식으로 암호화
+ -in plainpassword.txt -out encryptpassword.bin : plainpassword.txt 파일을 encryptpassword.bin 로 암호화하여 저장.

3.  파일 내용 확인

```cat encryptpassword.bin```

4. openssl 을 사용하여 encryptpassword.bin 을 decryptpassword.txt 파일로 복호화

```openssl enc -d -des3 -in encryptpassword.bin -out decryptpassword.txt```

+ enc -d -des3 : des3 방식으로 복화화
+ -in encryptpassword.bin -out decryptpassword.txt : encryptpassword.bin 파일을 decryptpassword.txt 로 복호화하여 저장.

5. 복호화된 파일의 내용 확인

```cat decryptpassword.txt```
