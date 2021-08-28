# Start a dev server
> Serve a local directory of static assets - using one-line solutions and no scripts

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
1. Open your repo in VS Code.
1. Start the server.
    - In the bottom right of the IDE, click the "Go live" button to start (or stop) the server.
    - Or open the command-prompt pop-up in the IDE and find "Live Server: Open with live server".
1. Open your browser (this should launch automatically).
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

The Python CLI and the Python standard library are light and easy. No need to install a package or write a script!

Approaches to choose from using the `http.server` module.

- Start in the current directory on port 8000 by default - view on `http://localhost:8888`.
    ```sh
    $ python3 -m http.server
    ```
- Specify a port and restrict to localhost for security.
    ```sh
    $ python3 -m http.server 8080 --bind 127.0.0.1
    ```
- Start in a subdirectory, such as `docs` here. The brackets makes the commands run in a _subshell_, so that you remain in same directory as before when the command is stopped.
    ```sh
    $ (cd docs && python3 -m http.server)
    ```

I like to alias the command like this:

```sh
alias pserver='python3 -m http.server'
```

Then run it:

```sh
$ pserver
```


## Node

There are many ways to do this.

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
- [serve](https://www.npmjs.com/package/serve)
    - > Static file serving and directory listing 
    - This was recommended to me by React CLI when doing a build.
    - Created by the Vercel team.
    - Serves on port 5000.
    - Commands.
        Global install.
        ```sh
        $ npm install -g serve
        $ serve
        $ serve build -s
        $ serve -p 8080 
        ```
        Without installing.
        ```sh
        $ npx serve
        ```
- [sirv](https://www.npmjs.com/package/sirv) and [sirv-cli](https://github.com/lukeed/sirv/tree/master/packages/sirv-cli)
    > You may use sirv as a very fast and lightweight alternative to `serve-static`.
    ```sh
    $ npm i sirv -g
    $ sirv build
    $ sirv build --port 8080 --cors --single
    ```
- [glance](https://www.npmjs.org/package/glance)
- [harp](http://harpjs.com/)
- [serve-static](https://www.npmjs.com/package/serve-static)

Notes:

- Single-Page App mode like React, some support a flag like `-s,--single`, that is for . All not-found requests will go to `index.html`.
- CORS mode - enable CORS to set `Access-Control-Allow-Origin` to `*`.


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