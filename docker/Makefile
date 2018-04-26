TAG="k-kitchen:latest"

build:
	docker build -t ${TAG} --force-rm .

run:
	docker run --rm -it ${TAG}

clean:
	docker rmi ${TAG}
