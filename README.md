# Premise WP Docker Environment

This idea is for us to have a very easy to set up WP environment which both clients and devs
will also be able to run locally on their own machines, with identical environments,
needing only to install docker.

## Setup

1.  Install docker.
    Mac: https://store.docker.com/editions/community/docker-ce-desktop-mac
    Windows: https://store.docker.com/editions/community/docker-ce-desktop-windows

2.  If it's a new project, create a .secrets file in the root directory and export
    the relevant environment variables (see docker-compose).
    Otherwise, request the .secrets from the project manager and store it in the root directory.

3.  cd to the project directory and run docker-compose to fetch and start the images.

```sh
$ cd /your/path/to/premise-wp
$ docker-compose up
```

> This could take some time to run, depending on your internet speed...

4.  Visit http://localhost:8000 to view the site, or to complete the 5 minute installation
    if this is a new project.

### Notice

_You can close and restart docker and the containers, and the database will persist.
Running_

```sh
$ docker-compose down --volumes
```

_**will remove the database**_
