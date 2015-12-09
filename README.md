To run private docker registry server:

1. run `docker-compose build` on current folder.
2. run `docker-compose up -d` on current folder, this will initiate a docker container named **docker-registry-server** in local system docker host, and it will bind port 5000 to local system.

On docker client side to access this private registry server, use **[host_ip]:5000** as *REGISTRY_HOST:REGISTRY_PORT* mentioned in docker official help.