# Example Page

This is a package of html page that helps your debugging for analytics tools.

## How to run

### Create SSL cert
```sh
mkdir keys
openssl genrsa 2048 > keys/server.key
openssl req -new -key keys/server.key > server.csr
openssl x509 -in keys/server.csr -days 1825 -req -signkey keys/server.key > keys/server.crt
```

### Build
```sh
docker build -t test-page .
```

### Run

```sh
docker run -d --name test-page -p 443:443 -p 80:80 test-page
```
