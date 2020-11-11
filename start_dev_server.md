# Start a static web server in a target directory
> Using one-line solutions instead of scripts

The first solution uses an IDE extension and the rest involve using the command-line (intended for macOS and Linux, but they will hopefully work on Windows too).


## Live Server extension

1. Install VS Code's [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension.
2. Open your repo in VS Code.
3. In the bottom right, click the "Go live" button to start (or stop) the server at the root of your repo.
4. Open the browser at:
    - http://localhost:5500/

Notes on this solution:

- Works on any OS.
- This doesn't require installing Node, Python, PHP, etc. or working with the CLI, like the options below. 
- Hot reloading - the browser will refresh to reload a page if you change a file.
- The downside is that this only works on port `5500` and requires to use VS Code as your IDE and have it open. The options below can be run in a terminal anywhere by anyone, as long as they have the correct dependencies.


## Python

Install Python 3 - follow [gist](https://gist.github.com/MichaelCurrin/57caae30bd7b0991098e9804a9494c23).

Start in the current directory on http://localhost:8888 server.

```sh
python3 -m http.server
```

Add a port and restrict to localhost.

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
# OR
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
