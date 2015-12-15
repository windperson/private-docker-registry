To run private docker registry server
------

1. run `docker-compose build` in this folder.
2. run `docker-compose up -d` in this folder, a docker container named **docker-registry-server** will run in local system docker host, and it will bind port 5000 to local system.

On docker client side to access this private registry server, use **[host_ip]:5000** as *REGISTRY_HOST:REGISTRY_PORT* mentioned in docker official help,

And be sure to add [--registry-mirror=http://[host_ip]:5000](https://github.com/docker/distribution/blob/master/docs/mirror.md#configuring-the-docker-daemon) startup parameter in client side docker engine.

**Note**: 

* Since it is a pure http conduit registry server, so be sure to add [--insecure-registry](https://docs.docker.com/registry/insecure/#deploying-a-plain-http-registry) startup parameter in client-side docker engine.
* Currently there's no way to remove cached docker images in the [volume](https://docs.docker.com/engine/userguide/dockervolumes/#data-volumes) called *registry_data*, which is the data volume of private registry server.

<hr/>

To run cli utiltiy to fetch current stored image infomation in private docker registry server
------

1. run `docker build -t=docker-registry-search cli` on current folder.
2. run  `docker run --rm docker-registry-search [host_ip]:5000 list all` to list all docker image stored in that registry server.