# Continuous Deployments using Spinnaker on AWS and Kubernetes

<br/>

### Local kubernetes + local spinnaker

<br/>

**Vagrantfile for 3 node cluster**

https://github.com/webmakaka/vagrant-kubernetes-3-node-cluster-centos7


<br/>

**Vagrant VM Network Settings fot Spinnaker**

    $ vagrant plugin install vagrant-hostmanager

    $ cd vagrant
    $ vagrant up

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

    $ {
        sudo systemctl restart apache2
        sudo systemctl restart gate
        sudo systemctl restart orca
        sudo systemctl restart igor
        sudo systemctl restart front50
        sudo systemctl restart echo
        sudo systemctl restart clouddriver
        sudo systemctl restart rosco
    }


<br/>

![Application](/img/pic2.png?raw=true)

<br/>

![Application](/img/pic3.png?raw=true)

<br/>

![Application](/img/pic4.png?raw=true)

<br/>

https://raw.githubusercontent.com/in4it/node-demo-app/master/demo-app.yml

<br/>

![Application](/img/pic5.png?raw=true)


---

<a href="https://marley.org"><strong>Marley</strong></a>