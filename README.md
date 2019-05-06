# Docker Swarm

## Create docker machine
```
docker-machine create -d virtualbox manager1
```

or 

```
docker-machine create manager
docker-machine create agent1
docker-machine create agent2
```

## Check docker machine status

```
docker-machine ls
```

## ssh docker machine

```
docker-machine ssh
```

## Get IP Address of docker machine
```
docker-machine ip manager1
```

## Create docker swarm

```
docker swarm init
```

```
export manager_token=`docker swarm join-token manager -q`
export worker_token=`docker swarm join-token worker -q`
```

## Create services using docker-compose

```
docker stack deploy -c <xxx.yml> <service_name>
```

## Check services

```
docker stack services <service_name>
docker stack ps <service_name>
```



## Remove all docker swarm services

```
docker service rm $(docker service ls -q)
```

## Remove all docker machines

```
docker-machine rm -f $(docker-machine ls -q)
```

## Create docker service
```
docker service create -p 80:80 --name web nginx:latest
```

## List docker node 
```
docker node ls
```

## Inspect docker service
```
docker service inspect web
```

## Scale docker service
```
docker service scale web=10
```

## Check docker service
```
docker service ps web
```

## Set docker node inactive
```
docker node update --availability drain manager1
```

## Set docker node active
```
docker node update --availability active manager1
```

## Check docker logs
```
docker service logs <SERVICE ID>
```


## Force to leave docker swarm
```
docker swarm leave --force
```
