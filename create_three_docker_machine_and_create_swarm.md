```
docker-machine create manager
docker-machine create agent1
docker-machine create agent2
```


```
docker swarm init --advertise-addr `docker-machine ip manager`
```

```
docker-machine ssh agent1 docker swarm join --token `docker swarm join-token -q worker` `docker-machine ip manager`:2377
docker-machine ssh agent2 docker swarm join --token `docker swarm join-token -q worker` `docker-machine ip manager`:2377
```

```
docker node ls
```
