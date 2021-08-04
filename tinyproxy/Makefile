IMAGE_NAME ?= rsysio/tinyproxy
IMAGE_TAG ?= latest

build:
	docker build -t $(IMAGE_NAME) .

test:
	docker run -it --rm -p 8888:8888 $(IMAGE_NAME)

shell:
	docker run -it --rm --entrypoint /bin/bash $(IMAGE_NAME)

push:
	docker push $(IMAGE_NAME):$(IMAGE_TAG)
