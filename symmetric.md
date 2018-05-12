# 대칭키 데모

위의 그림을 통해 살펴보면 동일한 암호키를 통해 암호화(Encryption), 복호화(Decryption)하는 것을 볼 수 있는데, 대칭키를 사용하는 암호화 알고리즘은 AES와 DES가 대표적이다. 본문은 RSA를 이용한 서명과 암호화의 활용 방법을 전달하는 것이 주된 목적이기 때문에 대칭키를 이용한 암호화 알고리즘에 대한 자세한 설명은 생략한다.

openssl을 통해 구체적으로 암호화, 복호화되는 과정을 살펴보도록 하자
plain.txt라는 파일의 내용을 DES3 알고리즘을 통해 암호화하는 과정이다. 예시로 암호화를 위한 패스워드는 123456 이라고 가정한다. 암호화된 결과는 cipher.bin를 통해 저장한다.

$ echo '안녕 프로그래밍' > plain.txt
$ openssl enc -e -des3 -in plain.txt -out cipher.bin
enter des-ede3-cbc encryption password: 123456
Verifying - enter des-ede3-cbc encryption password: _
암호화된 cipher.bin은 기존의 내용을 식별할 수 없는 상태이다.

$ cat cipher.bin
Salted__�Bd����������m��LoS�t��ɽҝ��J
마지막으로 DES3 알고리즘을 통해 복호화하는 과정이다. 암호화에 사용한 패스워드를 통해 아래와 같이 동일한 평서문을 얻을 수 있다.

$ openssl enc -d -des3 -in cipher.bin -out hola.txt
enter des-ede3-cbc decryption password: 123456
$ cat hola.txt
안녕 프로그래밍
OpenSSL(https://www.openssl.org/)은 TLS/SSL 프로토콜을 구현하는 오픈소스 프로젝트이다. OpenSSL에서는 TLS/SSL 프로토콜을 위한 다양한 암호화와 서명 기법을 제공한다.
