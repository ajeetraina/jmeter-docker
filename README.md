# jmeter-docker
<h1>Setting up JMeter under Swarm Mode</h1>

<b>Pre-requisite:</b>

1. Installing Docker 17.03 on all the cluster of nodes
2. Setting up Swarm Mode Cluster( running atleast 1 master and n-number of Slave Nodes)
3. Installing Docker Compose on the master node

<b>1. Installing Docker 17.03 on all the cluster of nodes:</b>

                $curl -sSL https://get.docker.com/ | sh

<b>2. Setting up Swarm Mode Cluster:</b>

<b>On Master Node:</b>

              $docker swarm init --listen-addr <master-ip>:2377 --advertise-addr <master-ip>:2377

<b>On Slave Node:</b>

              $docker swarm join --token <TOKEN> master-ip  <-- Run this command on all the slave nodes

<b>3. Installing Docker Compose on the master node:<b>

            $curl -L https://github.com/docker/compose/releases/download/1.11.2/docker-compose-`uname -s`-`uname -m` > /usr/local 
              /bin/docker-compose
              $chmod +x /usr/local/bin/docker-compose

<b> Pulling the Repository </b>

Login to master node and pull the repository:

                $git clone https://github.com/ajeetraina/jmeter-docker
                $cd jmeter-docker

<b>Running Docker Compose</b>

                $docker-compose up -d

It will push jmeter-master to the master node and jmeter-server to the slave nodes and make it ready to start load using the external JMX file.











