# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: vgongora <marvin@42.fr>                    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/10/09 12:33:24 by vgongora          #+#    #+#              #
#    Updated: 2019/10/09 17:19:39 by vgongora         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# -ADD --> 
# https://stackoverflow.com/questions/1078524/how-to-specify-the-location-with-wget

FROM debian

RUN apt-get update &&\
		apt-get upgrade &&\
		wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 &&\
