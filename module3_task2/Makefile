build: ## comment
	hugo

clean: ## cleans up package an build
	rm -r dist/*
	rm -r awesome-website.zip

post: ## comment
	hugo new posts/$(POST_NAME).md
	sed -i 's/title: .*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

help: ## comment
	cat Makefile | grep "##" | tr -d '##'


package: ## This command line download a zip archive to zip.
	make build
	zip awesome-website.zip dist/

lint: ## setup check
	markdownlint README.md
	markdownlint DEPLOY.md
	$(SHELLCHECK) setup.sh >/dev/null 2>&1 || "Lint Failed"
