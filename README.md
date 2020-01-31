# Docker: Ngingx with multiple Wordpress + MySQL 5.7. Using docker-compose and Dockerfile. 

## Architecture
- **Nginx proxy:** An Nginx proxy that listens on the port 80 and dinamically sign up new websites attached to the network.
- **Wordpress containers:** Each Wordpress container defined by a docker-compose.yml config, and a Dockerfile included in its own folder.
- **Database containers:** Each website can have its own database, or multiple of them can share one.

> Websites can be in their own docker-compose files too. They just need to be connected to the Nginx proxy network for this architecture to work as expected.

## Adding domains

In the `docker-compose.yml` file, using `website_db` and `website_wordpres` for reference, add the containers for your website and - if needed - database.

Then, create a folder inside `public/` with the name of the website. Three folders are expected inside:
- `.ssh` with the private keys to interact with remote repositories (defined in Dockerfile) - Only needed for repos cloned from external repositories.
- `mysql` empty folder that will contain the database. For shared databases, move it to it's own folder, don't forget to update the main docker-compose.yml.
- `www` folder to contain the web files. By default, an empty folder is expected. A repo will be cloned here. You can change this behaviour by editing the `command` used in the containers configuration inside the `docker-compose.yml` file.


## Installation

```bash
docker network create nginx-proxy-network       # Only required for the first domain
docker-compose up -d
```


> Batman vs Superman is a good movie 😝.