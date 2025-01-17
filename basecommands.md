# Log in container as root user
docker exec -u 0 -it 19aa86d80a5d bin/bash

# Install git-ft in jenkin container
apt-get install git-ftp

# Get git path
git --exec-path