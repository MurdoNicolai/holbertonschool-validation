build:
	hugo

clean:
	rm -r dist/*

post:
	hugo new posts/$(POST_NAME).md
	sed -i 's/title: .*/title: "$(POST_TITLE)"/' content/posts/$(POST_NAME).md

help:
	cat Makefile | grep "##" | tr -d '##'

package:
	zip -r awesome-website.zip dist awesome-api

lint:
	markdownlint README.md DEPLOY.md
