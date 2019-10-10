# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: vgongora <marvin@42.fr>                    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/10/09 12:33:24 by vgongora          #+#    #+#              #
#    Updated: 2019/10/10 17:29:18 by vgongora         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# -ADD --> opies new files, directories, or remote file URLs from <src> and adds them to the filesystem of the image at the path 
# -WORKDIR --> sets ythe working directory for any RUN CMD ENTRYPOINT COPY and ADD
# -EXPOSE -->
# -ENV -->
# https://docs.docker.com/engine/reference/builder/#workdir
# https://stackoverflow.com/questions/1078524/how-to-specify-the-location-with-wget

## Building and running the created image from the dockerfile
# https://hub.docker.com/_/teamspeak
# docker build -t ex01 .
# docker run -it ex01 -p 9987:9987/udp -p10011:10011-p 30033:30033 -eTS3SERVER_LICENSE=accept ex01

#FROM debian

#RUN apt-get update
#RUN apt-get install bzip2
#RUN apt-get install ca-certificates -y

#WORKDIR /opt

#RUN adduser --disabled-password --gecos "" teamspeak
#RUN mkdir teamspeak
#RUN chown -R teamspeak:teamspeak teamspeak/

#ADD https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 opt

#RUN tar -xvf teamspeak3-server_linux_amd64-3.9.1.tar.bz2
#RUN mv teamspeak3-server_linux_amd64 teamspeak

#RUN chown -R ts3server  teamspeak3
#RUN adduser --disabled-password --gecos "" teamspeak
# create admin
#RUN chown -R teamspeak:teamspeak teamspeak

# license agreement
#ENV TS3SERVER_LICENSE=accept

#USER = teamspeakadmin

# Voice port
#EXPOSE 9987/udp
# FTP port
#EXPOSE 30033
# ServerQuery
#EXPOSE 10011

#WORKDIR teamspeak

# ts3server_minimal_runscript.sh
#  **cd $(dirname $([ -x "$(command -v realpath)" ] && realpath "$0" || readlink -f "$0"))
#  **exec ./ts3server $@

#ENTRYPOINT sh ts3server_minimal_runscript.sh

# FRANS

#FROM , gets the base image, FROM scratch
#FROM debian
#RUN, will execute commands in/from the base image
#RUN apt-get update
#RUN apt-get install bzip2 -y
#RUN apt-get install ca-certificates -y
#RUN adduser --disabled-password --gecos "" teamspeak
#RUN mkdir /opt/teamspeak
#RUN chown -R teamspeak:teamspeak /opt/teamspeak/
#ADD https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 .
#RUN tar -xvf teamspeak3-server_linux_amd64-3.9.1.tar.bz2
#RUN mv teamspeak3-server_linux_amd64/* /opt/teamspeak/
#RUN rm -rf ./teamspeak3-server_linux_amd64*
#EXPOSE 9987/udp
#EXPOSE 30033
#EXPOSE 10011
#ENV TS3SERVER_LICENSE=accept
#WORKDIR /opt/teamspeak
#ENTRYPOINT sh ts3server_minimal_runscript.sh

#MONDE

FROM debian
ENV TS3DIR=/opt/teamspeak
RUN apt-get update && apt-get upgrade -y && apt-get install bzip2 wget apt-utils ca-certificates -y --no-install-recommends && rm -rf /var/lib/apt/lists/* && \
wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 -O /tmp/teamspeak.tar.bz2 && \
tar jxf /tmp/teamspeak.tar.bz2 -C /opt && \
mv /opt/teamspeak3-server_* ${TS3DIR} && \
rm /tmp/teamspeak.tar.bz2 && \
rm -rf /var/lib/apt/lists/*
RUN groupadd -g 503 teamspeakadmin && \
useradd -u 503 -g 503 -d ${TS3DIR} teamspeakadmin && \
mkdir /data && \
chown -R teamspeakadmin:teamspeakadmin ${TS3DIR} /data
ENV TS3SERVER_LICENSE=accept
USER teamspeakadmin
# Voice port
EXPOSE 9987/udp
# FTP port
EXPOSE 30033
# ServerQuery
EXPOSE 10011
WORKDIR $TS3DIR
ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh"]
### Build server
# docker build -t ex01 .
### Run
# docker run -dit --init --rm --name ts3 -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ex01
### Launch Teamspeak Client and Connect to 192.168.99.100:9877
