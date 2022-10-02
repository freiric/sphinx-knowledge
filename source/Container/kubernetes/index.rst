Kubernetes
=============

Required package:

- kubelet
- kubeadm
- kubectl
- container runtime - Docker

layer-2 layer-3 connectivity vs overlay network.

Distribution
*******************

- `Kind <https://kind.sigs.k8s.io/>`_
- minikube 

Packaging
***********
- `Helm <https://helm.sh/>`_

Tools
*********
`K9s <https://github.com/derailed/k9s>`_

.. image:: imgs/screen_po.png


Architecture
***************

- Master
  
  - apiserver (Rest / json) (through kubectl)
  - cluster store (etcd (=distributed value store))
  - controller manager
  - scheduler

- Nodes

  - kubelet:
    register node with cluster, watches apiserver, instantites pods, reports to master, exposes port 10255 /healthz, /spec
    
  - container engine: pulling images, starting/stopping container: docker, coreos rocket
  - kube-proxy: assign an ip per pod, load-balancing between pods of a service

- pods, only one ip per pods

- service, owns a snigle ip and dns name, and loads balance between its pods=
  
  - select its pods by labels
  - only sends to healthy pods
  
- deployment > replication controller -> replicas set

Command Line
*************

.. code-block:: shell
   :caption: creation/ informations about

   kubectl create -f myfile.yml
   kubectl get pods

.. code-block:: yaml
   :caption: yml file
	     
   apiVersion: v1
   kind: [pod, replicationController, Service]
   metadata:
      name: blabla
      labels:
	  zone: prods
	  version: v1
   spec
      replicas: 5
      template:
         spec:
	     containers:
	     - image: blob-hello-world
