Introduction to DevOps: Automate Everything to Focus on What Really Matters


Tasks:
0)

    Use the theme “ananke” for the website by following the section Note for non-git users at the Step 3
    Usage of Git Submodules is prohibited: there should be no file .gitmodules
    The website title should be “Awesome Inc.”
    The contents consists in a single blog post which title should be “Welcome to Awesome Inc.”, stored in a file named welcome.md
    All of the website’s source code is stored under a directory named module1_task0
    The command line hugo in version 0.80.0 must be used
    The website is expected to be generated into the directory module1_task0/dist/
    The directory module1_task0/dist/ must not be committed (it should be absent from the repository)

example:

➜ ls -l dist/ 2>/dev/null | wc -l
0
➜ hugo > /dev/null 2>&1
➜ ls dist/ 2>/dev/null | grep -c 'index.html'
1


1)


    Same requirements as the previous task:
        A Valid Go-Hugo website is provided
        There are no Git Submodules
        The theme ananke is installed
        No directory dist/ committed

    GNU Make version 3.81 or 4.0 must be used

    The “Build” step should be executed by the command make build, “Clean” by make clean and “Post” by make post.


example:
➜ ls -1 ./dist/
➜ make build
➜ ls -1 ./dist/index.html
index.html

➜ ls -1 ./content/posts/
welcome.md
➜ make POST_NAME=who-are-we POST_TITLE="Who are we" post
➜ ls -1 ./content/posts/
welcome.md who-are-we.md

➜ make clean
➜ ls -1 ./dist/

2)



    Same requirements as the previous task:
        A Valid Go-Hugo website is provided
        There are no Git Submodules
        The theme ananke is installed
        No directory dist/ committed
        Makefile present

    Add comments in the Makefile to describe what each target is expected to do.
        These comments should be written on the same line as the targets
        Each comment should start with two characters #

Here is a Makefile example:

cook:     ## Prepare a meal in the current kitchen
    cook ./kitchen

    Add a “help” target to the Makefile which prints out the list of targets and their usage.
        Ideally the usage should be the comment associated with each target

With the same previous example:

➜ make help
cook: Prepare a meal in the current kitchen
help: Show this help usage

    Add (or update) a README.md file located at the repository’s root
        A section named “Prerequisites” is expected to describe the requirements for this website (GoHugo, etc.)
        A section named “Lifecycle” is expected to describe the different steps

➜ cat README.md | grep -c "## Prerequisites"
1
➜ cat README.md | grep -c "## Lifecycle"
1

3)


    Write a shell script named setup.sh to reproduce a pseudo “production” environment locally
        The script must be executable
        The script must execute the “Production Instructions”
        The script file is located at the root of your project, along with the Makefile
    The script should be executed in a disposable Ubuntu 18.04 environment
        You can spawn a sandboxed environment with the following command (with Docker): docker run --rm --tty --interactive --volume=$(pwd):/app --workdir=/app ubuntu:18.04 /bin/bash and use the command exit to quit (and delete) the environment.
    The result of the script execution should be the same as what is described by your colleague: it must exit with the error code from Make and prints the full error in the stdout.

➜ grep 'UBUNTU_CODENAME' /etc/os-release
UBUNTU_CODENAME=bionic
➜ command -v hugo >/dev/null 2>&1 || echo "No 'hugo'"
No 'hugo'
➜ ./setup.sh >/dev/null 2>&1
➜ echo $?
255
➜ command -v hugo >/dev/null 2>&1 || echo "No 'hugo'"
➜ ./setup.sh 2>&1 | grep -c "recipe for target 'build' failed"
1


4)


    Update the shell script named setup.sh
        The script must be executable
        The script file is located at the root of your project, along with the Makefile
    The script should be executed in a fresh Ubuntu 18.04 environment
        You can spawn a sandboxed environment with the following command (with Docker): docker run --rm --tty --interactive --volume=$(pwd):/app --workdir=/app ubuntu:18.04 /bin/bash and use the command exit to quit (and delete) the environment.
    The result of the script execution should be successful (with an exit code 0) with the directory ./dist containing the generated website.

➜ grep 'UBUNTU_CODENAME' /etc/os-release
UBUNTU_CODENAME=bionic
➜ command -v hugo >/dev/null 2>&1 || echo "No 'hugo'"
No 'hugo'
➜ ls -l dist/ 2>/dev/null | wc -l
0
➜ ./setup.sh >/dev/null 2>&1
➜ echo $?
0
➜ hugo > /dev/null 2>&1
➜ ls dist/ 2>/dev/null | grep -c 'index.html'
1
