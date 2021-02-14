# Keycloak AWS

### generate a self-signed cert using the keytool
```
keytool -genkey -alias localhost -keyalg RSA -keystore keycloak.jks -validity 3650 -ext SAN=dns:localhost,dns:ec2-52-67-60-255.sa-east-1.compute.amazonaws.com
```

### convert .jks to .p12
```
keytool -importkeystore -srckeystore keycloak.jks -destkeystore keycloak.p12 -deststoretype PKCS12
```

### generate .crt from .p12 keystore
```
openssl pkcs12 -in keycloak.p12 -nokeys -out tls.crt
```

### generate .key from .p12 keystore
```
openssl pkcs12 -in keycloak.p12 -nocerts -nodes -out tls.key
```

### set permissions
```
chmod 777 tls.*
```

### Then use the tls.crt and tls.key for volume mount /etc/x509/https
### Also, on the securing app, specify the following properties
```
keycloak.truststore=classpath:keystore/keycloak.jks
keycloak.truststore-password=secret
```
### generate image
```
docker-compose build
```
