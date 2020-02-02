# Example Page

This is a package of html page that helps your debugging for analytics tools.

## How to run

### Create SSL cert
```sh
mkdir keys
openssl genrsa 2048 > keys/server.key
openssl req -new -key keys/server.key > keys/server.csr
openssl x509 -in keys/server.csr -days 1825 -req -signkey keys/server.key > keys/server.crt
```

### Build
```sh
docker build -t nginx-local-test .
```

### Run

```sh
docker run -d --name Web -p 443:443 -p 80:80 nginx-local-test
```
