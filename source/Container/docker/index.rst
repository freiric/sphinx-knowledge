Docker
==========

Based on cgroups and namespaces...

.. code-block:: shell

   docker containter ls # list of running containter
   docker start -it run sh #  start a conatiner and run a termina while attaching standard input/output
   docker exec -it containerid sh # execute a command (here a terminal) in a running container 
   docker inspect ...

.. code-block:: shell

   journalctl -u docker.service
   
exit a container, without termintaing it
CTRL + p + q

swarm mode vs single engine mode

ingress load = balancer?

raft consensus
Layer 7 load-balancing

ipvmac requires promiscuous mode  on guest nic @network


docker stack (prev dopcker compose)
++++++++++++++++++++++++++++++++++++

The ``docker stack`` is integrated ion docker since vers. 1.12 and replace ``docker-compose`` except it does not build images.

.. code-block:: shell

   docker-compose -f docker-compose up

   docker swarm init
   docker stack deploy -c docker-compose.yml somestackname


docker networkin
+++++++++++++++++


- CNM (container networking model)
  competitor is CNI (container networking interface) which is Kubernetes version

  - Sandbox (nemespace under linux)
  - endpoint (interface, e.g. eth0)
  - network (connected endpoints)
  
- libnetwork
  iplementation of CNM
- driver,   network specific details
  
  - overlay
  - bridge
  - MACVLAN
  - IPVLAN


.. code-block:: sh

   docker networ ls

Scope is either local (single-host) or swarm (multi-host)   
