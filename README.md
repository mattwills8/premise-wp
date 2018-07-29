# Premise WP Docker Environment

This idea is for us to have a very easy to set up WP environment which both clients and devs
will also be able to run locally on their own machines, with identical environments,
needing only to install docker.

## Setup

1.  Install docker.

    - Mac: https://store.docker.com/editions/community/docker-ce-desktop-mac
    - Windows: https://store.docker.com/editions/community/docker-ce-desktop-windows

2.  If it's a new project, create a secrets/ directory in the root and
    add a new .txt file there for each relevant environment variable (see docker-compose).
    Otherwise, request the secrets/ from the project manager and store it in the root.

3.  cd to the project directory and run docker-compose to fetch and start the images.

```sh
$ cd /your/path/to/premise-wp
$ docker-compose up
```

> This could take some time to run, depending on your internet speed...

### Notice

_You can close and restart docker and the containers, and the database will persist.
Running_

```sh
$ docker-compose down --volumes
```

_**will remove the database**_

## Usage

- Visit http://localhost:8000 to view the site, or to complete the 5 minute installation
  if this is a new project.

- Visit http://localhost:8080 to open phpmyadmin. You can do everything you want here
  as you normally would on a MAMP installation.

  The db data is stored as a volume, meaning it actually lives on your local machine,
  not within the container, and docker just has its own access to it.
  This gives us the ability to safely restart the mysql container without losing anything.

## Development

- wp-content is stored as a volume, so effectively it will stay in sync inside and outside
  the container. It actually lives outside the container (in the project root), so deleting the container or
  the image won't affect it.

  _**Beware:**_ Reinstalling or updating the wp core could overwrite wp-content.
  Make sure you have it backed up and saved in a different location before running
  anything that will affect the wp core.

  Since wp-content is a volume, we can make changes to it either manually or via Wordpress
  (eg by installing a plugin) and it will always stay in sync.

## Resources

- Docker overview: https://docs.docker.com/engine/docker-overview/#docker-engine
- Wordpress Docker Image: https://hub.docker.com/_/wordpress/
- MySQL Docker Image: https://hub.docker.com/_/mysql/
- Docker Volumes: https://docs.docker.com/storage/volumes/
