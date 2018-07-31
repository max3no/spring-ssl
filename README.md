# Spring starter ssl

## Getting Started

Need jdk, spring boot, working machine.

### Prerequisites

Install Spring Boot.
Configure your java in environmental variables.


### Steps

Create a new Spring Starter Project (Dependency - Web)

```
https://start.spring.io/
```
We use the keytool application present in the folder -

```
\jdk1.8.0_131\bin\keytool.exe
```

Create a new folder, open cmd use this command to create a certificate
Note - not recommended in prod, use trusted 3rd party to generate certificates in production, only used for dev and POC

```
keytool -genkey -alias selfsigned -storetype PKCS12 -keyalg RSA -keysize 2048 -keystore mykeystore.jks -validity 360
```
enter the answers to the questions then asked, remember the password.
A certificate with name mykeystore.jks is created, copy it in your resource folder and then

add the following setting in application.properties

```
server.port=8443
server.ssl.key-store=classpath:mykeystore.jks
server.ssl.key-store-password=[yourpassword]
server.ssl.key-password=[yourpassword]
```
Run the application with the new port using https

```
https://localhost:8443/welcome
```

## Acknowledgments

* Open Source community
