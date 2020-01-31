FROM wordpress:php7.1


################# GLOBAL TOOLS #################
USER root
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y apt-utils
RUN apt-get install -y git
RUN apt-get install -y screen
RUN apt-get install -y htop
RUN apt-get install -y sudo
RUN apt-get install -y sudo
RUN apt-get install -y ssh


################# SET UP REPOSITORY #################
RUN mkdir -p /root/.ssh/
ADD .ssh/id_rsa /root/.ssh/id_rsa
RUN touch /root/.ssh/known_hosts
    # ONLY NEEDED FOR BITBUCKET.ORG
RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts     
# RUN git clone git@bitbucket.org:User/repo.git /
# RUN git -C /var/www/html clone https://github.com/WordPress/WordPress.git