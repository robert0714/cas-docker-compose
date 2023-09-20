# CAS Docker Compose
* When we started up docker ,we saw the messages "/etc/cas/thekeystore not found" .
```bash
docker compose up -d
```
* So we have to enter container to generate the certificate about HTTPS . 

```bash
docker exec -it   cas  bash

keytool -genkey -alias youhoucas -keyalg RSA -validity 3650 -keystore ./thekeystore -keypass changeit -storepass changeit -dname "CN=localhost,OU=TDD,O=TDD55,L=Robert,ST=Robert,C=ZH"

docker cp cas:/tmp/thekeystore .
```

* When we restart docker , we use browser the url ``https://localhost/cas/login``.we use the below username and password :
  * username: casuser
  * password: Mellon

