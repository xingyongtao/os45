
.PHONY: all docker docker-image

all: docker

docker-image: Dockerfile hd.img
	docker build -t helloos:10.0.0 .

docker: docker-image
	docker run --rm -it --name helloos-10  helloos:10.0.0