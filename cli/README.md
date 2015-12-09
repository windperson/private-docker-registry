# docker_registry_cli

Docker Registry CLI - Currently ONLY Supports the Search capability via Catalog API in the new version of Docker Registry v2. 

Features :
===

1. List all the repos available on Docker Registry
2. Search for repositories
3. Supports HTTPS and Basic Auth enabled Docker Registry

Prerequisities
===

1. Download the new Docker Registry 2.1+ that supports Catalog API

Usage:
===

1. To use the CLI : 

  `python browser.py <REGISTRY_ENDPOINT> <keyword> <options>`

  REGISTRY_ENDPOINT : `<IP_ADDRESS_DOCKER_REGISTRY>:<PORT>` eg: localhost:5000

  keyword :

  + *search* - allows searching for Docker Images. Supports partial search. No RegEx Support yet. 

  eg:

    `python browser.py localhost:5000 search busybox`

    `python browser.py localhost:5000 search busy`

    `python browser.py localhost:5000 search bu`


  + *list* - lists all the Docker images available in the Image Registry with their respective tags 

  eg:- 
  
    `python browser.py localhost:5000 list all`


2. To use the Dockerfile, refer to the following examples :

1. `docker build -t <imagename> .`

2. `docker run -p 5000:5000 -d <imagename>  localhost:5000 search busybox`

Examples:

```
$ docker build -t docker_reg_search .

$ docker run docker_reg_search localhost:5002 list all

-----------

Name: busybox

Tags: v1	v2	latest

-----------

Name: busyy

Tags: v2

-----------

Name: jenkins

Tags: latest


$ docker run docker_reg_search localhost:5002 search bus

-----------

Name: busybox

Tags: v1	v2	latest

-----------

Name: busy

Tags: v2

```

**Support for SSL and Authenticated Docker Registry**

If the Docker registry is only authenticated via SSL

`python browser.py localhost:5000 search busy ssl`
`python browser.py localhost:5000 list all ssl`

If the Docker registry is authenticated by Username and Password, but not via SSL

`python browser.py exampleuser:exampleuser@localhost:443 search busybox`
`python browser.py exampleuser:exampleuser@localhost:5000 list all`

If the Docker registry is authenticated by both Username:Password, and SSL 

`python browser.py exampleuser:exampleuser@localhost:443 search mobile ssl`
`python browser.py exampleuser:exampleuser@localhost:5000 list all ssl`

Please note that currently the python script does not verify the SSL Certificate. It also does not suppress the SSL warning. The `ssl` flag is only used to toggle the URL protocol as https. 