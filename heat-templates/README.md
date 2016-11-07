# midas-cloud
Heat templates and image building scripts for deploying MIDAS on an OpenStack cloud

To deploy on LCRC OpenStack:

    # Set up your OpenStack environment
    source openrc

    # Use Heat to launch the cluster, parameterized with:
    # - 4 workers
    # - all instances using m1.xlarge flavor
    heat stack-create -f midas.yaml -P midas_worker_count=4 -P flavor=m1.xlarge midas
