calibre-server-docker
=====================

Docker container with calibre preinstalled

Getting the image
-----------------
You can pull it from "9z3eu/calibre-server" or clone it from "https://github.com/steff333/calibre-server.git"

All you need is the Dockerfile.


Using your library
------------------

This container exposes the volume **/opt/calibre/server** and the port **8080**


To allow calibre to run **your library** you have to **mount it as a volume** with ``-v /your/library/location:/opt/calibre/library``


Running the container
------------------------

    docker run -p 80:8080 -v /media/calibre/books:/opt/calibre/library -name calibre 9z3eu/calibre-server

From now on:

    docker start calibre


You can pass arguments to calibre-server:

    docker run -p 80:8080 -v /media/calibre/books:/opt/calibre/library -name calibre 9z3eu/calibre-server --username user --password pass

