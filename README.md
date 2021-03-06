To run private docker registry server
------

1. run `docker-compose build` in this folder.
2. run `docker-compose up -d` in this folder, a docker container named **docker-registry-server** will run in local system docker host, and it will bind port 5000 to local system.

On docker client side to access this private registry server, use **[host_ip]:5001** as *REGISTRY_HOST:REGISTRY_PORT* mentioned in docker official help.

* **Note**: since it is a pure http conduit registry server, so be sure to add [--insecure-registry](https://docs.docker.com/registry/insecure/#deploying-a-plain-http-registry) startup parameter in client-side docker engine.

<hr/>

To run cli utiltiy to fetch current stored image infomation in private docker registry server
------

1. run `docker build -t=docker-registry-search cli` on current folder.
2. run  `docker run --rm docker-registry-search [host_ip]:5001 list all` to list all docker image stored in that registry server.