# Ansible_kubernetes_multinode_cluster
"📌 Ansible Role to Configure K8S Multi Node Cluster over AWS Cloud.
🔅 Create Ansible Playbook to launch 3 AWS EC2 Instance
🔅 Create Ansible Playbook to configure Docker over those instances.
🔅 Create Playbook to configure K8S Master, K8S Worker Nodes on the above created EC2 Instances using kubeadm.
🔅 Convert Playbook into roles and Upload those role on your Ansible Galaxy. 
🔅 Also Upload all the YAML code over your GitHub Repository.
🔅 Create a README.md document using markdown language describing your Task in creative manner. 
🔅 Create blog about task and share on your LinkedIN profile.

Here is the blog link descriping entire things https://krithikasharma2129.medium.com/ansible-role-to-configure-k8s-multi-node-cluster-over-aws-cloud-9598c93b826d

**Steps for launching the Kubernetes multinode cluster**
1. Both the nodes (master and slave) require docker containers. The master node needs containers for running different services, while the worker node needs them for the client to launch the pods.
2. Now the next step is to install the software for K8s setup which is kubeadm, but by default, kubeadm is not provided by the repos configured in the yum, so we need to configure yum first before downloading it.
3. Installing kubelet, kubectl, kubeadm, and iproute-tc. Start the kubelet service. All the services of the MasterNode are available as containers and "kubeadm" can be used to pull the required images.
4. Docker by default uses a Cgroup Driver called "cgroupfs". But Kubernetes doesn't support this cgroup rather it supports the "systemd" driver. Hence, we must change this. Restart the Docker service
5. Copying k8s.conf file
6. Start the kubeadm service by providing all the required parameters.
7. We usually have a separate client who will use the kubectl command on the master, but just for testing, we can make the master the client/user. Now if you run the "kubectl" command, it will fail (we already have kubectl software in the system). The reason for the above issue is that the client doesn't know where the master is, so the client should know the port number of API, and username and password of the master, so to use this cluster as a normal user, we can copy some files in the HOME location, the files contain all the credentials of the master node.
8. Install Add-ons.
