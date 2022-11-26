* Create the Vagrantfile to deploy 1 master and 2 worker node VMs.
`vagrant up`

* Run the playbook to install and deploy kubernetes cluster including CNI and dashboard. Master and worker node IP's are need to define in hosts file.
`ansible-playbook -i hosts install-kubernetes.yaml`
