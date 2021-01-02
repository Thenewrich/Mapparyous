# Start a static web server in a target directory
> Using one-line solutions instead of scripts

The first solution uses an IDE extension and the rest involve using the command-line (intended for macOS and Linux, but they will hopefully work on Windows too).

**Table of contents**

- [Live Server extension](#live-server-extension)
- [Python](#python)
- [Node](#node)
- [PHP](#php)
- [Ruby](#ruby)


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
$ python3 -m http.server
```

Add a port and restrict to localhost.

```sh
$ python3 -m http.server 8080 --bind 127.0.0.1
```
   
Start in a subdirectory. The brackets means run in a subshell so you remain where you are when the command is stopped.

```sh
$ (cd docs && python3 -m http.server)
```


## Node

There are many ways to do this.

### Builtin

Using the builtin `http` library - from [tutorial](https://www.w3schools.com/nodejs/nodejs_http.asp).

- `index.js`
    ```js
    var http = require('http');

    http.createServer(function (req, res) {
      res.write('Hello World!');
      res.end();
    }).listen(8080); 
    ```

```sh
node index.js
```

### NPM packages

Here are a couple of packages to install and use.

- [http-server](https://www.npmjs.com/package/http-server)
    ```sh
    $ npm i -g http-server
    $ http-server -a localhost
    ```
- [simple-server](https://www.npmjs.com/package/simple-server)
    ```sh
    $ npm i -g simple-server
    $ simple-server public 3000
    ```
- [live-server](https://www.npmjs.com/package/live-server)
    > A great zero-config HTTP server with live reload capability.
    ```sh
    $ npm i -g live-server
    $ live-server
    ```
- [glance](https://www.npmjs.org/package/glance)
- [harp](http://harpjs.com/)


## PHP

```sh
$ php -S 127.0.0.1:8000
```

Or

```sh
$ php -S localhost:8080 -t .
```


## Ruby

```sh
$ ruby -run -e httpd . -p 8080
```


## References

These lists are more detailed and cover other solutions:

- [gist by @willurd](https://gist.github.com/willurd/5720255)
- [Simple One-line local HTTP servers](https://medium.com/sweetmeat/simple-one-line-local-http-servers-8adb57d93ec3) Medium.com post.
