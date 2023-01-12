build: #comment
	hugo

clean: #Cleanup the content of the directory `dist/`
	rm -r dist/*

post: #comment
	hugo new posts/$(POST_NAME).md
	sed -i 's/title: .*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

help: #comment
	cat Makefile | grep "##" | tr -d '##'

package: #comment
	zip -r awesome-website.zip ./dist ./awesome-api

lint: #comment
	markdownlint README.md DEPLOY.md
