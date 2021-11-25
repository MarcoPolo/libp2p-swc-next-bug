# Bug repro for SWC minify + js-libp2p

This highlights a bug that surfaces from using SWC minify (from Next.js) and
js-libp2p.

You get error you get when you dial a peer:
```
    Error: Error occurred during XX handshake: Cannot decode stage 1 MessageBuffer: length less than 80 bytes.
```

A couple notes:
* You don't get this error in dev mode (`yarn next dev`)
* You don't get this error if you disable swcMinify.


## Setup

```
yarn

yarn next build && yarn next export
cd out
# run you favorite webserver to serve this directory, I use simple-http-server:
nix run nixpkgs#simple-http-server -- -i -p 8081
```