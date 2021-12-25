# redis_demo
This repo stores redis config and application code.

Applications built for resiliency have backup options in case of application or infrastructure failures 

1. Create the redis cluster on --net redis all are using port 6379 default
2. create sentinel --net redis
3. docker network inspect redis
copy the i/p(which are obiviously private ip) of redis nodes and add those in hpproxy.cfg file. bind it on 6380 port
4. build and run the haproxy.
copy ip using docker network redis and search for haproxy container.
use this ip in python script to connect and port will be 6380

Workflow:
           +----+ 
           | W1 |    application
           +----+ 
             |   
             |   
             |   
        +---------+
        | HAProxy |
        +---------+
           /   \
    +----+ +----+  +----+
    | R1 | | R2 |  | R1 |    Redis servers
