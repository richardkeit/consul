# Consul Service Discovery

### Start to use Consul for maintenance and administration of RabbitMQ containers

#### Start a container as the first Consul node - automatic leader

`docker run -p 8400:8400 -p 8500:8500 -p 8600:53/udp -h node1 progrium/consul -server -bootstrap -ui-dir /ui
`

#### Start a container to join the existing cluster

Inspect existing node to get its IP address to join
`JOIN_IP="$(docker inspect -f '{{.NetworkSettings.IPAddress}}' node1)"`

`docker run -d --name node2 -h node2 progrium/consul -server -join $JOIN_IP`
