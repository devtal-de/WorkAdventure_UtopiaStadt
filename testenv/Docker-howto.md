# How to Docker/Podman

Run in current directory (testenv):

    podman build -t workadv-srv .
    podman run --rm -it -p 10443:443 -v $(pwd)/..:/wa workadv-srv

You may replace podman by Docker if you wish.

Open <https://play.workadventu.re/_/global/localhost:10443/main.json> or
adjust this URL to fit your workadventure instance. 

## Implementation Notes

Caching on this test server is disabled, so you should always get the latest
configuration when reloading the workadventure. Files are served via HTTPS
using an selfsigned certificate automatically generated at container build
time. CORS is disabled, to fit all workadventure instances. Apache httpd is
used to serve files.
