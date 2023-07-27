# HTTPD Light Webserver

Really Small Static Webserver with minimum overhead for use in Kubernetes environments.
Using busybox and standard httpd and making a custom build that only holds the static binary (170KB).

## Run the image

```bash
docker build -t my-static-website .
docker run -it --rm -p 3000:3000 my-static-website
```

Browse to http://localhost:3000.

> Sending a TERM signal to your TTY running the container won't get propagated due to how busybox is built. Instead you can call docker stop (or docker kill if can't wait 15 seconds). Alternatively you can run the container with docker run -it --rm --init which will propagate signals to the process correctly.

## Busybox httpd config

https://git.busybox.net/busybox/tree/networking/httpd.c
