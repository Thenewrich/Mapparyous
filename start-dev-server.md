# Start a dev server
> Serve a local directory of static assets - using one-line solutions and no scripts

<!-- This file exists as gist rather than in a repo or on a site, so it makes it more predictable to link to from multiple repos without worrying about the link breaking. -->

The first solution uses an IDE extension, while the rest involve using the command-line (intended for macOS and Linux, but they will hopefully work on Windows too).

**Table of contents**

- [IDE extension](#ide-extension)
- [Python](#python)
- [Node](#node)
- [PHP](#php)
- [Ruby](#ruby)


## IDE extension

Install a live server extension for your IDE.

Most web developers tend to use VS Code, so I'll cover that.

1. Choose one of these, go to the page, and click "Install" there.
    - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension. Supports a preview in your browser only.
    - [Live Preview](https://marketplace.visualstudio.com/items?itemName=ms-vscode.live-server) extension by Microsoft. Supports a preview in the IDE or in your browser. This actually uses the Simple Browser command which is already built-in to VS Code.
1. Open your repo in VS Code.
1. Start the server.
    - In the bottom right of the IDE, click the "Go live" button to start (or stop) the server.
    - Or open the command-prompt pop-up in the IDE and find one of:
       - "Live Server: Open with live server"
       - "Live Preview: Start server"
1. Open your browser (this should launch automatically). For Live Preview, you can skip this step and use the preview pane in VS Code.
    - http://localhost:5500/

Notes:

- This works on any OS.
- No environment set up needed. No need for installing or learning to CLI commands for runtimes (Node or Python), or any packages (like from NPM).
- Includes hot-reloading - the browser will refresh to reload a page if you change a file. The Live Preview one even reloads on every change you type, without having to save.
- Open a file like `index.html` before starting the server to get the browser to open there. Or you will get a folder view of your directory, which is also fine.
- You might want to install a browser debugger extension for Chrome or Firefox so you can get your debugging in your IDE to work as usual.
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

Some popular options:

```sh
$ npx serve
```

```sh
$ npx sirv
```

Here are a couple of NPM packages you can choose from.

- [Static web servers](https://michaelcurrin.github.io/dev-cheatsheets/cheatsheets/javascript/packages/static-web-servers.md)


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
