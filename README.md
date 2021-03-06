# patchlite

A browser client for the Scuttlebutt network

_work in progress_

## Setup

Install Scuttlebot (your gossip server)

```sh
npm install scuttlebot@latest -g

# make sure you have secure-scuttlebutt@15.2.0
npm ls secure-scuttlebutt -g

sbot server
# if you are already running patchwork, that also works.
# (must have at least >= 2.8)

# then in another tab (these must be separate commands)
sbot plugins.install ssb-links
sbot plugins.install ssb-query
sbot plugins.install ssb-ws
sbot plugins.install ssb-fulltext # for faster searches (optional)

# restart sbot server (go back to previous tab and kill it)
```

Set a WebSocket port in your config file (`~/.ssb/config`).

``` json
{
  "ws": {
    "port": 8989
  }
}
```

Install Patchlite (a browser interface for the your scuttlebutt database)

```sh
git clone https://github.com/ssbc/patchlite.git
cd patchlite
npm install
```

Make sure scuttlebot is allowing private connections. Stop any running sbot server, restart it with the `--allowPrivate` option and create a new modern invite:

```sh
sbot server --allowPrivate
sbot invite.create --modern
```

From inside the Patchlite repo folder, run:

```sh
npm start
```

This will build an html file at `build/index.html` and start a static file server on local port `8000`.

Browse to <http://localhost:8000#> with your invite code appended on the end of the address. (`#ws://localhost:8989...`)

You should see a page load and then automatically refresh, that is the invite being consumed.

When you load the page again, you will be loading your feed from your local `sbot` over a WebSocket, it will take some time.

If you want to change your key or remote configuration, enter `/config` in the "location bar" (top-right text field).

## license

AGPL-3.0
