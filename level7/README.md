## Level 7 load balancing

It happens at the HTTP layer. It has access to ports, ip, data. It is a software that acts as a load balancer.

Pros:
1. Smart load balancing.
2. Caching.
3. Great for microservices.

Cons:
1. Expensive - looks at the data.
2. Decrypts (SSL termination).
3. Two TCP connections.
4. Must share TLS certificate.

## How to run the example

This demo app will run 2 simple node apps in docker containers on ports `3000` and `4000` - but these are not exposed to the public so you can't access them. 
Both of these apps have a HAProxy level 4 load balancer infront of them that runs a publicly available url `http://localhost:8000`.

execute `docker-compose up` and then visit `http://localhost:8000`

You will notice that visiting `http://localhost:8000` each time will server request from a different backend server i.e. it will divide the load using a round robbin strategy.