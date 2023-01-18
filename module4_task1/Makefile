build: ## comment
	docker run awesome:build hugo
	docker run awesome:build touch awesome-api

clean: ## cleans up package an build
	docker run awesome:build rm -r dist/*
	docker run awesome:build rm -r awesome-website.zip
	docker run awesome:build rm coverage-units.out coverage-integrations.out

post: ## comment
	docker run awesome:build hugo new posts/$(POST_NAME).md
	docker run awesome:build sed -i 's/title: .*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

help: ## comment
	docker run awesome:build cat Makefile | grep "##" | tr -d '##'


package: ## This command line download a zip archive to zip.
	docker run awesome:build make build
	docker run awesome:build zip awesome-website.zip ./dist/

lint: ## setup check
	ls
	## markdownlint README.md
	## markdownlint DEPLOY.md

unit-tests: ## test not working
	docker run awesome:build echo "make integration-tests"
	docker run awesome:build echo "make validate"
	docker run awesome:build touch coverage-units.out

integration-tests: ## test not working
	docker run awesome:build touch coverage-integrations.out

build-docker: ## makes image: awsome:build
	docker build ./build -t awesome:build --no-cache

test: ## run tests
	docker run awesome:build make unit-tests
	docker run awesome:build make integration-tests

