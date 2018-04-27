TAG="k-kitchen:latest"
BRANCH ?= "master"

build:
	git clone --branch $(BRANCH) ssh://git@github.com/explodingbarrel/sparx-cookbooks.git volumes/sparx-cookbooks/
	docker build -t ${TAG} --force-rm .

run:
	docker run --mount type=bind,source=${PWD}/volumes/sparx-cookbooks,target=/cookbooks --rm -it ${TAG}

lint:
	-docker run --mount type=bind,source=${PWD}/volumes/sparx-cookbooks,target=/cookbooks --rm -w /cookbooks/cookbooks --entrypoint /usr/bin/foodcritic ${TAG} .

clean:
	-docker rmi ${TAG}
	-rm -rf volumes/sparx-cookbooks/
