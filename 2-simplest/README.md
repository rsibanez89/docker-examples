A docker container that uses a bash script to print.

# To build
Run > dos2unix script.sh
Run > chmod +x script.sh
Run > docker build .
Run > docker run --name 2-simplest <build number>

# To build with a tag
Run > docker build -t 2-simplest .
Run > docker run 2-simplest

# To inspect files system in the docker container
Run > docker build -t 2-simplest .
Run > docker run -ti 2-simplest sh

# To remove
Run > docker rm 2-simplest