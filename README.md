# terraform_k8s

this repo is going to contain code that spins up a bunch of openstack VMs using terraform, and then spews out a bunch of docker instances onto them using kubernetes.

this is being done so I can learn some new skills, and work towards learning a new way to parallelise work.

eventually I intend to use this code to do some parallel machine learning with spark and MLlib stuff.


terraform needs the following:

**a tf.vars file**, which literally just defines a bunch of variables for terraform to use

**a tf file**, which gets all the vars needed and runs some stuff to make the openstack instances

### Best practices:

anti-affinity groups. 

 - one of the magical things about cloud computing is if one of the instances dies, I can just get a new one. this doesnt work so well if all my instances are on one bit of hardware, and then that dies. this is one of the reasons to use anti-affinity groups - by ensuring that all instances are hosted on different bits of hardware, we introduce some resilience and redundancy.
 - another reason to use anti-affinity groups is so that you can use load-balancers?
 - check the above statement, i think you might be reading a dodgy article pal.
 
 
 kubernetes cluster:
 
 needs networking
 
 has either control-plane or node roles for servers
 
 uses pods - which is basically a container (or set of containers) that is being managed by kubernetes
 
 
 
 ### Terraforming to make machines for k8s
 
 I will need a bunch of hosts
 
 I will need networking
 
 I will need some ports open for networking
 
 I will need some ports open for etcd networking
 
 
 
 
 
 I will want to have a service, which is a way of grouping pods together into 1 object
