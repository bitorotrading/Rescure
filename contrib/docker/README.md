### Setup docker on Debian 8.1

Install notes: https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository

Docker CLI: https://docs.docker.com/engine/reference/run/

Script that installs docker-ce: `setup_docker_debian.sh`

### Build&Run RECUR docker container

Pre: `RecurPay.conf MUST be available under link RECUR_CONF_URL as pointed out in the Dockerfile`

Build container: `sudo docker build --tag recur:1.0.3 .`

Run container: `docker run -d --name recur.cont recur:1.0.3`

See if it is up: `docker ps -a`

Shell in the container: `docker exec -it recur.cont /bin/bash`

Test RPC: `recur-cli -rpcuser=recur -rpcpassword=<from config file> help`

Stop container: `docker stop recur.cont`

Delete container: `docker rm recur.cont`