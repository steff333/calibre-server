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

    docker run -p 80:8080 -v /media/calibre/books:/opt/calibre/library -name calibre 9z3eu/calibre-server --shutdown-timeout=300

Restricting access to the serivce
------------------------

It is possible to restrict access to the server to authorized users only. To do so you must define the user and their rights in the desktop application under 
   Preferences -> sharing of the net.
As a result a SQLite-database file is created in your calibre home directory (e.g. ~/.config/calibre/server-users.sqlite). 
To use this file, mount the folder with your database file as well and start the container with 
    docker run -p 80:8080 -v /media/calibre/books:/opt/calibre/library -v ~/.config/calibre:/opt/calibre/config --name calibre-server 9z3eu/calibre-server --userdb /opt/calibre/config/server-users.sqlite --enable-auth

