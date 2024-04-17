Docker Setup
=================


* Running Order for External Parameters:

> 1.  run.sh
> 2.  docker.compose
> 3.  conf.utils
> 4.  deploy.conf.template
> 5.  deploy.conf


* Executing Order for running a docker image:

> 1.  Execute {./build-docker.sh}
> 2.  Edit {docker-compose.yml} tp setup ports and no. of servers
> 3.  Startup a {docker-compose up -d}
> 4.  docker-compose ps??
> 5.  deploy.conf

* Useful Commands:    

> 1.  docker images
> 2.  docker ps  -a
> 2.  docker stop {imageID}
> 3.  docker rm {imageID}
> 4.  docker logs -f e8c51aa247b64840dd1f319ec7e64739598a3764aa94c802b1991b46f8ceda60
> 5.  list all running containers = docker ps
> 6.  list all running containers = docker ps -l
> 7.  docker logs -f e3b6c | tee result92009

* Looking up Docker on the DEV Machine!!
>1. ssh  -i ".pem" centos@10.23.126.45
>2. sudo docker --tls ps -a
>3. sudo  docker --tls ps -a | grep sales-report
>4. sudo  docker --tls logs 25aad
>
* Looking up Docker on the DEV Machine FOR SUBSCRIPTION!!
>1.  ssh -i neo-dev.pem centos@10.23.127.83
>2.  sudo docker --tls ps -a
>3. sudo docker --tls logs -f [Container ID]


Docker Inspect
