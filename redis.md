# Redis



```
brew install redis
    $ redis-server
    $ redis-cli
    
#connecting to remote Redis server
#IP address & port
$redis-cli -h XXX.XXX.XXX.XXX -p YYYY


#Using Docker
Redis Example:
$ docker run --name redisdb -p 6000:6379 redis
$ docker exec -it redisdb redis-cli

$ docker exec -it redisdb /bin/bash 
```

