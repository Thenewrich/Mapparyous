# Start a static web server in a target directory
> Using one-line solutions instead of scripts


## Python

Install Python 3 - follow [gist](https://gist.github.com/MichaelCurrin/57caae30bd7b0991098e9804a9494c23).

Start in the current directory on http://localhost:8888 server.

```sh
python3 -m http.server
```

Add port and restrict to localhost.

```sh
python3 -m http.server 8080 --bind 127.0.0.1
```
   
Start in a subdirectory. The brackets means run in a subshell so you remain where you are when the command is stopped.

```sh
(cd docs && python3 -m http.server)
```

## Node

### HTTP-server

```sh
npm install http-server -g
http-server -a localhost
```

- https://www.npmjs.org/package/glance
- http://harpjs.com/


## PHP

```sh
php -S 127.0.0.1:8000
```

Or

```sh
php -S localhost:8080 -t .
```

## Ruby

```sh
ruby -run -e httpd . -p 8080
```

## References

These lists are more detailed and cover other solutions

- [gist](https://gist.github.com/willurd/5720255)
- [Simple One-line local HTTP servers](https://medium.com/sweetmeat/simple-one-line-local-http-servers-8adb57d93ec3)


## IDE

Use VS Code's _Live Server_.