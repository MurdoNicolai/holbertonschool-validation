# Prerequisites

* Shell terminal basics

* Git with the command line
* Make/Makefile usage
* A HTML5-compliant web browser
* A free account on GitHub, referenced as `<GitHub Handle>`
* A shell terminal with `bash` `zsh` or `ksh`, including the standard Unix tool

set (`ls`, `cd` etc.) with:

* GNU Make in version 3.81+
* Git (command line) in version 2+
* `Go Hugo` v0.80+
* A text editor or IDE (Integrated Development Editor) of your convenience

(Visual Code, Notepad++, Vim, Emacs, IntelliJ, etc.)

## Lifecycle

* `build` : Generate the website from the markdown and configuration files in
  the directory `dist/`.
* `post` : Create a new blog post whose filename and title come from the
  environment variables `POST_TITLE` and `POST_NAME`.
* `help` : prints out the list of targets and their usage.
* `package` : make a zipfile with dis and the api
* `lint` : checks readme and deploy
* `clean` : cleans up package or build
* `build-docker`: builds virtual machine to run the website on
* `docker-tests`: tests docker

## Workflow

This project needs the following tools / services:

* The command lines
* yq
* shellcheck

## Build Workflow

Regarding the tooling, you have to:

* Ensure that the workflow is executed into an Ubuntu 18.04
  execution environment
* Ensure that all the required tools are installed prior to any make target,
  by executing the script setup.sh
* The script should be modified to only install missing tools (no make target
  are expected)
