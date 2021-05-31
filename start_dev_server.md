# Start a dev server
> Serve a local static directory of assets - using one-line solutions and not scripts

<!-- This file exists as gist rather than in a repo or on a site, so it makes it more predictable to link to from multiple repos without worrying about the link breaking. -->

The first solution uses an IDE extension, while the rest involve using the command-line (intended for macOS and Linux, but they will hopefully work on Windows too).

**Table of contents**

- [Live Server extension](#live-server-extension)
- [Python](#python)
- [Node](#node)
- [PHP](#php)
- [Ruby](#ruby)


## Live Server extension


1. Install VS Code's [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension.
2. Open your repo in VS Code.
4. Start the server.
    - In the bottom right of the IDE, click the "Go live" button to start (or stop) the server.
    - Or open the command-prompt pop-up in the IDE and find "Live Server: Open with live server".
5. Open your browser (this should launch automatically).
    - http://localhost:5500/

Notes:

- Works on any OS.
- This doesn't require installing Node, Python, PHP, etc. or working with the CLI, like the options below. 
- Includes hot reloading - the browser will refresh to reload a page if you change a file.
- Open a file like `index.html` before starting the server to get the browser to open there. Or you will get a folder view of your directory, which is also fine.
- Limitations:
    - This only works on port `5500` and requires to use VS Code as your IDE and have it open. The alternatives below can be run in a terminal anywhere by anyone (without VS Code installed), as long as they have the correct dependencies.
    - If your `index.html` page and assets are at the **root** of your repo, this works great. But this does **not** work properly if you have assets in a subdirectory because that extension will serve from the root. e.g. If your homepage is in `public/index.html`, then the browser will open at `http://127.0.0.1:5500/public/index.html`, then looking for `/styles.css` will fail. But, you can change the root - a way around this is to open your serving directory as a new window in VS Code. e.g. `code public` and then start the server in that window.


## Python

Install Python 3 - follow [gist](https://gist.github.com/MichaelCurrin/57caae30bd7b0991098e9804a9494c23).

The Python CLI and the Python standard library are sufficient here - no need to install a package or write a script.

Approaches to choose from:

- Start in the current directory on port 8000 by default - view on `http://localhost:8888`.
    ```sh
    $ python3 -m http.server
    ```
- Specify a port and restrict to localhost.
    ```sh
    $ python3 -m http.server 8080 --bind 127.0.0.1
    ```
- Start in a subdirectory. The brackets makes the commands run in a subshell, so that you remain in same directory as before when the command is stopped.
    ```sh
    $ (cd docs && python3 -m http.server)
    ```


## Node

There are many ways to do this.

### Built-in

Using the built-in `http` library - from [tutorial](https://www.w3schools.com/nodejs/nodejs_http.asp).

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

Here are a couple of packages you can choose from.

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
- [serve-static](https://www.npmjs.com/package/serve-static)
- [sirv](https://www.npmjs.com/package/sirv) and [sirv-cli](https://github.com/lukeed/sirv/tree/master/packages/sirv-cli)
    > You may use sirv as a very fast and lightweight alternative to serve-static.
    ```sh
    $ npm i -g sirv
    $ sirv build --port 8080 --cors --single
    ```
- [serve](https://www.npmjs.com/package/serve)
    - This was recommended to me by React CLI when doing a build.
    - > Static file serving and directory listing 
    - Commands
        ```sh
        $ npm install -g serve
        $ serve -s build
        ```


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
