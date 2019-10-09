# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: vgongora <marvin@42.fr>                    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/10/09 11:16:40 by vgongora          #+#    #+#              #
#    Updated: 2019/10/09 17:01:23 by vgongora         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# A dockerfile is practically a Makefile for docker, it builds a usabe an image
# -FROM --> always starts with this so as to get a base image to work off of
# -RUN --> executes any command given on the image and commit the results
# -ENTRYPOINT --> allows you to configure a container that will run as an execuable (vim is this case)
# -CMD --> provide defaults for an executing container
#	**only the last ENTRYPOINT instructionint the dockerfile will have an effect

## Building and running the created image from the dockerfile
# https://hub.docker.com/_/alpine
# https://www.tutorialspoint.com/docker/building_docker_files.htm
# docker build -t ex00 . (name the image ex00: no specified tag format)
# dockr run -it ex00 (run image ex00)

FROM alpine

RUN apk update && apk upgrade && apk add vim

ENTRYPOINT vim
