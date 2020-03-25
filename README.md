# Continuous Deployments using Spinnaker on AWS and Kubernetes

<br/>

**Vagrantfile for 3 node cluster**

https://github.com/webmakaka/vagrant-kubernetes-3-node-cluster-centos7


<br/>

**Vagrant VM Network Settings fot Spinnaker**

<br/>

![Application](/img/pic1.png?raw=true)


localhost:9000


<br/>

**as ubuntu user**


    $ curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/

<br/>

    $ mkdir -p ~/.kube

    // root password: kubeadmin
    $ scp root@master:/etc/kubernetes/admin.conf ~/.kube/config

<br/>

    $ kubectl get nodes
    NAME         STATUS   ROLES    AGE   VERSION
    master.k8s   Ready    master   95m   v1.17.4
    node1.k8s    Ready    <none>   92m   v1.17.4
    node2.k8s    Ready    <none>   89m   v1.17.4


<br/>

###  Enable kubernetes

    $ hal config provider kubernetes enable

    $ hal config provider kubernetes account add my-k8s-v2-account \
        --provider-version v2 \
        --context $(kubectl config current-context)

    $ sudo hal deploy apply

<br/>

    $ git clone https://github.com/webmakaka/spinnaker-course

    $ cd spinnaker-course/scripts/
    $ ./6-restart-spinnaker.sh

<br/>


https://raw.githubusercontent.com/in4it/node-demo-app/master/demo-app.yml


<br/>

![Application](/img/pic2.png?raw=true)