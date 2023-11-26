---
title: "How to Create an AWS Elastic Kubernetes Service (EKS) Cluster"
datePublished: Sun Dec 18 2022 22:30:54 GMT+0000 (Coordinated Universal Time)
cuid: clbtxzia9000b08mp9g3r4qtx
slug: how-to-create-an-aws-elastic-kubernetes-service-eks-cluster
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671816086662/ba9ad733-47da-49be-9147-dc11ea49542d.png
tags: aws, kubernetes, eks, elastic-kubernetes-service, eks-cluster

---

We will be explaining steps to follow to create to create an AWS EKS cluster.

**Set Up The IDE or Command Line Interface**

The first step to start from in creating an EKS cluster on AWS is to set up the interfaces and Integrated Development Environments (IDE) to enable communication with AWS APIs. You can set up the AWS Command Line Interface (AWS CLI) on your local machine or set up AWS Cloud9 (an IDE) on AWS. AWS CLI is preinstalled on Cloud9, unlike your local machine which requires the setting up of AWS CLI. If you want to know how to set up Cloud9, I have another blog post on how to do this [click here](https://henryeleonu.hashnode.dev/how-to-set-up-aws-cloud9-environment). You may follow the steps [click here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) to download and install AWS CLI and for these steps to configure AWS CLI [click here](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html).

**Install or Update kubeclt**

kubectl is a command line tool that you use to communicate with the Kubernetes API server. kubectl is available in many package managers and installation via a package manager is often easier than a manual download and install process. Steps for the installation of kubectl can be found in this link [click here](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html).

**Install or Update eksctl**

eksctl is a simple CLI tool for creating and managing clusters on EKS. It is written in Go, uses CloudFormation, and was created by Weaveworks. eksctl provides the fastest and easiest way to create a new cluster with nodes for Amazon EKS. As a prerequisite, kubectl must be installed before the installation of eksctl. This link [click here](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html) shows short steps to follow to install eksctl.

**Create an AWS EKS Role**

To enable your Kubernetes clusters managed by Amazon EKS to make calls to other AWS services and manage the resources on AWS, you must create an IAM role with the following policies: [AmazonEKSClusterPolicy](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1&skipRegion=true#/policies/arn:aws:iam::aws:policy/AmazonEKSClusterPolicy$jsonEditor) [Click here](https://docs.aws.amazon.com/eks/latest/userguide/service_IAM_role.html) to find the steps to create this role.

**Creating a VPC for your Amazon EKS cluster**

You may decide to create a VPC beforehand or create it during cluster creation. Follow these steps [click here](https://docs.aws.amazon.com/eks/latest/userguide/creating-a-vpc.html) to create a VPC beforehand.

**Create an EKS cluster**

To create the Kubernetes cluster, we will first write a manifest in a YAML file with the file name eksctl-cluster.yaml. This is the manifest I used to create the Kubernetes cluster on AWS. The YAML files used to create the EKS cluster can be found in my GitHub repository:

[https://github.com/henryeleonu/spark-kubernetes/tree/jupyter-spark-kube](https://github.com/henryeleonu/spark-kubernetes/tree/jupyter-spark-kube)

%[https://gist.github.com/henryeleonu/e395c72d413a2b7c8001f1d2cb839b32] 

I ran the following command on my terminal to create the cluster.

eksctl create cluster -f eksctl-cluster.yaml

After the creation of the cluster, I ran the following commands:

To get all contexts:

kubectl config get-contexts

To get the current context:

kubectl config current-context

To set the context to EKS cluster on AWS:

kubectl config use-context [henry@spark-nodes.eu-west-2.eksctl.io](mailto:henry@spark-nodes.eu-west-2.eksctl.io)

**Creating an IAM OIDC provider for your cluster**

A Kubernetes service account provides an identity for processes that run in a pod. If a pod needs access to AWS services, a service account is mapped to an AWS Identity and Access Management identity to grant that access. Your cluster has an OpenID Connect (OIDC) issuer URL associated with it. To use AWS Identity and Access Management (IAM) roles for service accounts, an IAM OIDC provider must exist for your cluster. Follow these steps [click here](https://docs.aws.amazon.com/eks/latest/userguide/enable-iam-roles-for-service-accounts.html) to create an IAM OIDC provider for your cluster.

**Deploy The Cluster Autoscaler**

Autoscaling is a function that enables automatic horizontal scaling of your resources, that is, scaling resources up or down to meet changing demands. This is a crucial Kubernetes function that would otherwise be difficult to achieve if performed manually.

Amazon EKS supports two autoscaling products. The Kubernetes Cluster Autoscaler and the Karpenter open-source autoscaling project. The cluster autoscaler uses AWS scaling groups, while Karpenter works directly with the Amazon EC2 fleet. We will be using cluster autoscaler.

The Cluster Autoscaler requires the following tags on your Auto Scaling groups so that they can be auto-discovered. If you used eksctl to create your node groups, these tags are automatically applied.

Key Value

[k8s.io/cluster-autoscaler/my-cluster](http://k8s.io/cluster-autoscaler/my-cluster) owned

[k8s.io/cluster-autoscaler/enabled](http://k8s.io/cluster-autoscaler/enabled) true

Create an IAM policy that grants the permissions that the Cluster Autoscaler requires to use an IAM role. Follow these steps here [click here](https://docs.aws.amazon.com/eks/latest/userguide/autoscaling.html) to create the role and policy.

To deploy the Cluster Autoscaler:

Follow the steps here [click here](https://docs.aws.amazon.com/eks/latest/userguide/autoscaling.html).

Download the Cluster Autoscaler YAML file by running the following command:

curl -o cluster-autoscaler-autodiscover.yaml [https://raw.githubusercontent.com/kubernetes/autoscaler/master/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml](https://raw.githubusercontent.com/kubernetes/autoscaler/master/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml)

Modify the YAML file and replace `<YOUR CLUSTER NAME>` with your cluster name. Also, consider replacing the cpu and memory values as determined by your environment

Run the command on the terminal to deploy the Cluster Autoscaler:

kubectl apply -f cluster-autoscaler-autodiscover.yaml
