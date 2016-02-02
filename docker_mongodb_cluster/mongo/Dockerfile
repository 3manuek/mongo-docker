FROM        ubuntu:14.04.1
MAINTAINER  Emanuel Calvo "3manuek@esdebian.org"
ENV REFRESHED_AT 2016-02-02

# Using https://docs.mongodb.org/master/tutorial/install-mongodb-on-ubuntu/?_ga=1.2426614.73074352.1454434959 
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
RUN echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" |  tee /etc/apt/sources.list.d/mongodb-org-3.2.list
#Just in case, we have the binaries: RUN https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-ubuntu1404-3.2.1.tgz

# Install MongoDB using the 
RUN apt-get upgrade -yqq && \
  apt-get update -qq && \
  apt-get -yqq install mongodb-org && \
  apt-get -yqq clean

# Setting the data directory
RUN mkdir -p /data/db

# Exposing the default port
EXPOSE 27017

ADD js/initiate.js /initiate.js
ADD js/setupReplicaSet1.js /setupReplicaSet1.js
ADD js/setupReplicaSet2.js /setupReplicaSet2.js
ADD js/setupReplicaSet3.js /setupReplicaSet3.js
ADD js/addShard.js /addShard.js
ADD js/addDBs.js /addDBs.js
ADD js/enabelSharding.js /enabelSharding.js
ADD js/addIndexes.js /addIndexes.js
ADD start.sh /start.sh

CMD ["/start.sh"]
