TAG="k-kitchen:latest"
BRANCH ?= "master"
COOKBOOK_REPO="ssh://git@github.com/explodingbarrel/sparx-cookbooks.git"

build:
	git clone --branch $(BRANCH) ${COOKBOOK_REPO} ../volumes/sparx-cookbooks/
	docker build -t ${TAG} --force-rm .
	@echo "\n\033[0;36m#########################################################"
	@echo "\033[0;36m# Your cookbook development environment has been built. #"
	@echo "\033[0;36m#         Type '\033[0;31mmake run\033[0;36m' to start the container.       #"
	@echo "\033[0;36m# Your cookbook repository can be found at /cookbooks.  #"
	@echo "\033[0;36m#########################################################\033[0m\n"

run:
	@docker run \
	  --network host \
	  --privileged=true \
	  -v /var/run/docker.sock:/var/run/docker.sock \
	  -v ${HOME}/.gitconfig:/root/.gitconfig \
	  --mount type=bind,source=${PWD}/../volumes/sparx-cookbooks,target=/cookbooks \
	  --rm -it ${TAG}

lint:
	-docker run \
	  --mount type=bind,source=${PWD}/../volumes/sparx-cookbooks,target=/cookbooks \
	  --rm -w /cookbooks/cookbooks \
	  --entrypoint /usr/bin/foodcritic ${TAG} .

clean:
	-docker rmi ${TAG}
	-rm -rf ../volumes/sparx-cookbooks/
