<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launch a Kubernetes Cluster

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks1)

**Author:** Eric Gitau  
**Email:** gitaueric09@gmail.com

---

## Launch a Kubernetes Cluster

![Image](http://learn.nextwork.org/inspired_purple_vibrant_plum/uploads/aws-compute-eks1_e5f6g7h8)

---

## Introducing Today's Project!

In this project, I will deploy my first Kubernetes cluster using Amazon EKS, which is an AWS service for running Kubernetes in the cloud, and I will also learn how to use tools like eksctl and AWS CloudFormation.


### What is Amazon EKS? 

### One thing I didn't expect

### This project took me...

---

## What is Kubernetes?

Kubernetes is a tool for automating the management of containerized applications, also known as container orchestration, and it is used by companies and developers to deploy and manage applications at scale.


I used eksctl to create a Kubernetes cluster from the command line; the “eksctl create cluster” command I ran defined the cluster name, node group, node size, region, and the EC2 instance type.


I initially ran into two errors while using eksctl: the first was because eksctl was not installed yet, and the second was due to missing permissions on my EC2 instance to access my AWS account.


![Image](http://learn.nextwork.org/inspired_purple_vibrant_plum/uploads/aws-compute-eks1_ff9bfc221)

---

## eksctl and CloudFormation

CloudFormation helped create my EKS cluster because eksctl uses CloudFormation under the hood to provision the cluster resources; when I run the “eksctl create cluster” command, CloudFormation created VPC resources since using the default VPC for EKS could lead to networking compatibility and permission issues.


There was also a second CloudFormation stack for the node group. The difference between a cluster and a node group is that the cluster represents the entire Kubernetes setup, including the control plane, while the node group is simply a group of EC2 instances that act as worker nodes inside the cluster.


![Image](http://learn.nextwork.org/inspired_purple_vibrant_plum/uploads/aws-compute-eks1_w3e4r5t6)

---

## The EKS console

I had to create an IAM access entry to view the nodes in my new node group; an access entry is a mapping of AWS policies to Kubernetes access controls, and I configured it using the Access Entries page in the EKS Management Console.


It took about 30 minutes to create my cluster. Since I will create this cluster again in the next project in this series, I may be able to speed up the process in the future by using templates such as Terraform or CloudFormation and by installing dependencies in advance.


![Image](http://learn.nextwork.org/inspired_purple_vibrant_plum/uploads/aws-compute-eks1_e5f6g7h8)

---

## EXTRA: Deleting nodes

Did you know you can find your EKS cluster's nodes in Amazon EC2? 

This is because, in an AWS setup, EC2 instances act as the worker nodes in a Kubernetes cluster.


The desired size in a Kubernetes node group is the number of nodes we want to maintain, while the minimum and maximum sizes help ensure high availability during low traffic periods and prepare the cluster to handle increases in traffic when needed.


When I deleted my EC2 instances, Kubernetes automatically replaced them because the cluster is designed to maintain its desired state, which in this case is three nodes, ensuring that the required number of worker nodes is always running.


![Image](http://learn.nextwork.org/inspired_purple_vibrant_plum/uploads/aws-compute-eks1_q7r8s9t0)

---

---
