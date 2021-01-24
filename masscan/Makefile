IMAGE_NAME ?= rsysio/masscan
IMAGE_TAG ?= latest
TEST_CIDR ?= 10.0.0.0/8

build:
	docker build -t $(IMAGE_NAME) .

test:
	docker run -it --rm $(IMAGE_NAME) $(TEST_CIDR) -p 80

shell:
	docker run -it --rm --entrypoint /bin/bash $(IMAGE_NAME)

push:
	docker push $(IMAGE_NAME):$(IMAGE_TAG)
