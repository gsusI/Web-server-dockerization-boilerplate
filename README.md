# Boilerplate to dockerize a web server containing multiple websites.

## Architecture
- **Nginx proxy:** An Nginx proxy that listens on the port 80 and dinamically sign up new websites attached to its network.
- **Websites:** Each website has its own docker configuration, giving the flexibility to use whatever services it requires.

## Directory structure
```
.                                               - Repository root directory
    ./docker-config                             - Contains a folder for the proxy + a folder for each website.
        ./proxy                                 - The proxy config folder.
            ./docker-compose.yml                - Docker composer just for the proxy.
            ./config/my_proxy.conf              - Modify Nginx settings.
        ./example-website                       - Website config directory.
            ./docker-compose.yml                - An example website docker compose. Will generate all the containers needed for that web (except the proxy).
            ./config                            
                ./.ssh                          - SSH credentials for remote repositories
                ./Dockerfile                    - The Dockerfile for the Web container
```
## Adding domains

1. Create the storage folder for this new container (just clone storage/example-website and change the directory name).
2. Clone the example-website directory
    - Inside, adapt the following files to meet your specific needs:
        - `./docker-compose.yml`    Special attention to the volumes, which will need to point at the storage folder you previously created
        - `./config/Dockerfile`
    - Add your private SSH key to pull from remote repositories:
        - `./.ssh`

## Run

- Create the network: `docker network create nginx-proxy-network`
- Run the proxy: `cd docker-config/proxy && docker-compose up -d && cd ../../`
- Run the website: `cd docker-config/example-website && docker-compose up -d && cd ../../`
- Enjoy life: 🎈🍻🏂🍸🏖🎉


> Batman vs Superman is a good movie 😝.