# openshift on aws
## System Pre-Requisites 
https://docs.openshift.com/container-platform/3.10/install/prerequisites.html

## centos ami
https://aws.amazon.com/marketplace/pp/B00O7WM7QW

## SSH 
ssh -i "openshift.pem" centos@52.66.246.87

## install wget 
yum install wget 

yum install -y yum-utils device-mapper-persistent-data lvm2

yum install vim 

# docker installation 
https://docs.docker.com/install/linux/docker-ce/centos/#set-up-the-repository

## add docker ce repo 
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

yum install docker-ce

## start the docker 
systemctl start docker

## add insecure registries 
vim /etc/docker/daemon.json

{
   "insecure-registries": [
     "172.30.0.0/16"
   ]
}

## refresh something 
systemctl daemon-reload

## restart the docker 
systemctl restart docker

## download the oc 
wget https://github.com/openshift/origin/releases/download/v3.10.0/openshift-origin-client-tools-v3.10.0-dd10d17-linux-64bit.tar.gz

## up the cluster 
oc cluster up --public-hostname ec2-52-66-246-87.ap-south-1.compute.amazonaws.com --routing-suffix 52.66.246.87.nip.io
