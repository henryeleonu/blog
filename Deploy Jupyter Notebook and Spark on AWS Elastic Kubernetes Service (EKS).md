---
title: "Deploy Jupyter Notebook and Spark on AWS Elastic Kubernetes Service (EKS)"
datePublished: Tue Dec 20 2022 17:28:20 GMT+0000 (Coordinated Universal Time)
cuid: clbwi23j3000008jsatwudu7h
slug: deploy-jupyter-notebook-and-spark-on-aws-elastic-kubernetes-service-eks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671815627745/593527a0-9b1b-4546-8d72-33a7cb2e6483.png
tags: aws, spark, apache-spark, jupyter-notebook, eks

---

In this article, I am going to show the steps to follow to enable you to run Apache Spark on a cluster managed by Kubernetes. But before this, you have to first create the EKS cluster. I have another article on [how to create an EKS cluster in AWS](https://henryeleonu.hashnode.dev/how-to-create-an-aws-elastic-kubernetes-service-eks-cluster). Spark is a framework for big data processing which enables in-memory processing of a large amount of data by partitioning the data and distributing the partitions to the nodes that make up the cluster to be processed. The Dockerfile and YAML files used for the deployment of Spark on EKS can be found in my GitHub repository:

[**https://github.com/henryeleonu/spark-kubernetes/tree/jupyter-spark-kube**](https://github.com/henryeleonu/spark-kubernetes/tree/jupyter-spark-kube)

I also have a Youtube demo on the deployment of Spark on EKS.

%[https://www.youtube.com/watch?v=XGvdlSmNMvc] 

**Docker Image**

You will build a Spark docker image from a Dockerfile. The docker image is required to run the Spark docker containers in the Kubernetes cluster. Docker is a container runtime environment that is frequently used with Kubernetes. Spark ships with a Dockerfile that can be used to build the spark image. This Spark official Dockerfile can be customized to meet an individual application’s needs. The first step is to download Apache Spark from [https://spark.apache.org/downloads.html](https://spark.apache.org/downloads.html). Choose a package type: Pre-built for Apache Hadoop 3.3 and later. Then download the tar archive file to your local directory and extract it.

The next step is to build the Spark image. The Spark download has a `bin/docker-image-tool.sh` script that you can be used to build the Spark image found in the `kubernetes/dockerfiles/` directory. We will be building an additional Pyspark image with a docker file in this directory /kubernetes/dockerfiles/spark/bindings/python/Dockerfile

Example

```bash
# To build additional PySpark docker image
$ ./bin/docker-image-tool.sh -r <repo> -t my-tag -p ./kubernetes/dockerfiles/spark/bindings/python/Dockerfile build
```

Replace &lt;repo&gt; with the name of your docker hub repository and my-tag with the tag of the repository.

```bash
# To build additional PySpark docker image
$ ./bin/docker-image-tool.sh -r heleonu/spark-py -t 1.1 -p ./kubernetes/dockerfiles/spark/bindings/python/Dockerfile build
```

After building, push the image to docker hub using the command:

docker push heleonu/spark-py:1.1

You will create a Dockerfile that is based on the Spark base image we created earlier. This image which we will be using will have the packages and libraries we need such as Jupyter Notebook etc. You will build an image from this Dockerfile and push it to docker hub.

docker build -t heleonu/spark-py-kube:1.2 .

docker push heleonu/spark-py-kube:1.2

%[https://gist.github.com/henryeleonu/64b247a5e6471203cdd7a83f9841775d] 

**Create a Service Account and Permissions**

A service account provides an identity for processes that run in a Pod, and maps to a ServiceAccount object. A ClusterRole contains rules that represent a set of permissions. A ClusterRoleBinding grants the permissions defined in a ClusterRole to a user, groups, or service accounts. The YAML configuration below has the Service Account, ClusterRole and ClusterRoleBinding we used.

```bash
kubectl apply -f service-account.yaml
```

%[https://gist.github.com/henryeleonu/46e8a2505e82ab03d7aef98d50088baa] 

**Create Secret**

Kubernetes Secrets can be used to provide credentials for a Spark application to access secured services. The secret YAML file has the login credential spark required to communicate with the PostgreSQL database. The login credentials are encoded with base64 encoding. I have another article on [how to deploy PostgreSQL on EKS](https://henryeleonu.hashnode.dev/how-to-deploy-postgresql-on-aws-elastic-kubernetes-service-eks).

%[https://gist.github.com/henryeleonu/268516c3e68be13d77936bb459e0f6ff] 

Run the command to deploy the secret:

```bash
kubectl apply -f postgres-login-secret.yaml
```

**Creating Spark Pod**

You will create a spark pod with the YAML configuration below.

%[https://gist.github.com/henryeleonu/157c513a560d384cf05339549a9afb09] 

From the YAML file, the service account we created earlier is bound to the spark pod. We use the spark image, heleonu/spark-py-kube:1.2, which we created earlier. This command,

```yaml
command: ["jupyter", "notebook", "--ip", "0.0.0.0", "--allow-root"]
```

starts the Jupyter Notebook when the Spark container starts running. By default, Jupyter Notebook runs on port 8888. The secret is attached to the spark pod using these lines.

```yaml
envFrom:
          - secretRef:
              name: mysecret
```

Run the command to deploy the spark pod:

```bash
kubectl apply -f spark-pod.yaml
```

**Create Headless Service**

This headless service enables the spark executors to communicate with the spark driver.

%[https://gist.github.com/henryeleonu/e3c10027c1306aabf9f201c69b3e6e91] 

Run the command to deploy the headless service:

```bash
kubectl apply -f spark-headless-service.yaml
```

**Start Jupyter Notebook**

We may want to start Jupyter Notebook by Kubectl exec into the spark pod using the command

kubectl exec -it spark-pod bash

And then start Jupyter Notebook in the spark pod by running the command:

jupyter notebook --ip 0.0.0.0 --allow-root

When Jupyter Notebook starts in the spark pod it will display the URL on Jupyter Notebook on the terminal. This URL will have the port on which Jupyter Notebook is running in the pod. You need to port forward this port to enable you to run Jupyter Notebook on the browser on your local machine. You will open another terminal to do the port forwarding by running the command:

kubectl port-forward pod/spark-pod 8889:8889

This command assumes that Jupyter Notebook is running on port 8889 in the spark pod and this port is forwarded to port 8889 on your local machine. You can then copy the URL of Jupyter Notebook and paste it into the browser on your local machine to run it from your local machine. This way, you can submit Spark jobs to AWS EKS from your local browser. To better understand how this works, watch this YouTube demo.

%[https://www.youtube.com/watch?v=XGvdlSmNMvc] 

This is an example code to use on your notebook to set the spark configurations to enable the submission of Spark jobs on EKS.

%[https://gist.github.com/henryeleonu/2d2116f732c525159240c974001d7a01]
