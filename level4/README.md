## Level 4 load balancing

It happens at the Transport layer (TCP/UDP). We know the ports at Level 4. It is a software that acts as a load balancer. It receives the client's request and then decides which application server should receive the request.

Pros:
1. Simpler load balancing.
2. Efficient (no data lookup).
3. More secure (doesn't look at the data).
4. One TCP connection.
5. Uses NAT (Network Address Translation).

Cons:
1. No smart load balancing.
2. N/A to microservices. Microservices use level 7 load balancing like ingress.
3. Sticky per segment.
4. No caching (you don't know anything about the data). 

## How to run the example

This demo app will run 2 simple node apps in docker containers on ports `3000` and `4000` - but these are not exposed to the public so you can't access them. 
Both of these apps have a HAProxy level 4 load balancer infront of them that runs a publicly available url `http://localhost:8000`.

execute `docker-compose up` and then visit `http://localhost:8000`

You will notice that visiting `http://localhost:8000` will continue to display the same port in `Served by ....` message, i.e. it will be a sticky connection instead of a round robin, but if you stop the container and visit the page again then it will show you the other port number in `Served by ....` message.