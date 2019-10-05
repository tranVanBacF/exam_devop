Trần Văn Bắc
Bactv2
FHN.ICE

# Dockeefile

LABEL version="1.0"
RUN rm -rf /usr/local/tomcat/webapps/ROOT
COPY ROOT.war /usr/local/tomcat/webapps/

# create network
docker network create -d bridge --subnet 10.10.20.0/24 devop

# build image
docker build -t devop

# run container
docker run --network=devop -d --name=devop_server -p 8080:8080 devop

