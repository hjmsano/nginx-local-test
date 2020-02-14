# A sample plain website on nginx

This is a package of html page that helps your debugging for analytics tools.

## Build and Run

### A. From building an image

#### Create SSL cert
```sh
mkdir keys
openssl genrsa 2048 > keys/server.key
openssl req -new -key keys/server.key > keys/server.csr
openssl x509 -in keys/server.csr -days 1825 -req -signkey keys/server.key > keys/server.crt
```

#### Build
```sh
docker build -t nginx-local-test .
```

#### Run

```sh
docker run -d --name Web -p 443:443 -p 80:80 nginx-local-test
```

### B. Use the pre-built image

```sh
docker run -d --name Web -p 443:443 -p 80:80 hsano/nginx-local-test:latest
```

## Assign a directly of html files

- You can assign your local directly as a root of webpage by adding `-v {~/your/test/dir}:/var/html` option to `docker run` command.
- Or, you can configure it through Kitematic.

## Set a host name

- By adding a record to `hosts` file, you can host your testing page like `https://yourdomain/` (local only)
- A path to the hosts file is `/etc/hosts` on Linux and Mac, `C:\Windows\System32\drivers\etc\hosts` on Windows.
- Add a line like `127.0.0.1        test.example.com`, then try to access `https://test.example.com/` through your browser.
