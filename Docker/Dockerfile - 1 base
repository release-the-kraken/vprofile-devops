# base image for the container 
FROM ubuntu:latest
# add metadata to image
LABEL "Author"="Misiano"
LABEL "Project"="Crispy"
# execute commands 
RUN apt update
RUN apt install apache2 git -y
# run binaries/commands on docker run
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
# config for extra container that runs as an executable
#ENTRYPOINT
# define port for the container to listen on
EXPOSE 80
#set environment variables
#ENV
WORKDIR /var/www/html
# create mount point for external volumes
VOLUME /var/log/apache2
# add files and folders to the image - ADD copies and extracts packages etc.
ADD crispy.tar.gz /var/www/html/
# or
# COPY - just copies archives
#COPY


