# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dokerfile                                          :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: vgongora <marvin@42.fr>                    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2019/10/11 16:16:34 by vgongora          #+#    #+#              #
#    Updated: 2019/10/14 17:33:14 by vgongora         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# -ONBUILD --> instruction adds to the image a trigger instruction to be executed at a later time, when the image is used as the base for another build. The trigger will be executed in the context of the downstream build,  as if it had been inserted immediately after the FROM  instruction in the downstream Dockerfile.
#  **any build instruction can be registered as a trigger.
# http://www.xyzpub.com/en/ruby-on-rails/3.2/seed_rb.html
# https://stackoverflow.com/questions/54399362/your-ruby-version-is-2-6-0-but-your-gemfile-specified-2-5-0


##Steps:
# run container (linux  I believe)
# install ruby (research)
# create rails app
# run app and access it (localhost:3000)

fledwaba 5:15 PM
#https://docs.docker.com/compose/rails/
#https://guides.rubyonrails.org/getting_started.html
FROM ruby
RUN apt-get update
RUN apt-get install sqlite3 -y
RUN /bin/bash -l -c "gem install rails"
RUN apt-get install nodejs -y
RUN apt-get update
RUN apt-get install yarn -y
RUN rails new app
ADD https://raw.githubusercontent.com/rails/webpacker/master/lib/install/config/webpacker.yml app/config/
RUN mv app opt/
WORKDIR opt/app
EXPOSE 3000
#http://www.xyzpub.com/en/ruby-on-rails/3.2/seed_rb.html
RUN bundle install
RUN rake db:migrate
RUN rake db:seed
#docker build -t ft-rails:on-build .
#docker build -t ex02 .
#docker run -it --rm -p 3000:3000 ex02
