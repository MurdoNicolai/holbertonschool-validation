build: ## comment
	sudo curl -L https://github.com/gohugoio/hugo/releases/download/v0.91.2/hugo_0.91.2_Linux-64bit.deb -o hugo.deb
	sudo apt install -y ./hugo.deb
	hugo
	touch awesome-api

clean: ## cleans up package an build
	rm -r dist/*
	rm -r awesome-website.zip
	rm coverage-units.out coverage-integrations.out

post: ## comment
	hugo new posts/$(POST_NAME).md
	sed -i 's/title: .*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

help: ## comment
	cat Makefile | grep "##" | tr -d '##'


package: ## This command line download a zip archive to zip.
	make build
	zip awesome-website.zip ./dist/

lint: ## setup check
	ls
	## markdownlint README.md
	## markdownlint DEPLOY.md

unit-tests: ## test not working
	echo "make integration-tests"
	echo "make validate"
	touch coverage-units.out

integration-tests: ## test not working
	touch coverage-integrations.out

build-docker: ## makes image: awsome:build
	docker build ./build -t awesome:build --no-cache

test: ## run tests
	make unit-tests
	make integration-tests

