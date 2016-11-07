# midas-cloud
Heat templates and image building scripts for deploying MIDAS on an OpenStack cloud

To deploy on LCRC OpenStack:

    # Set up your OpenStack environment
    source openrc

    # Use Heat to launch the cluster, parameterized with:
    # - 4 workers
    # - all instances using m1.xlarge flavor
    heat stack-create -f midas.yaml -P midas_worker_count=4 -P flavor=m1.xlarge -P key_name=my-keypair midas-cluster

This deploy a cluster with one head node and *midas_worker_count* worker nodes.
The head node exports /home via NFS to the worker nodes, and runs the PBS server and scheduler.
The worker nodes mount the NFS share and run pbs_mom.

Jobs can be sumitted by logging in as the *centos* user to the head node. The head node IP can be displayed by running:

    heat stack-show midas-cluster

Terminate the cluster with:

    heat stack-delete -y midas-cluster
