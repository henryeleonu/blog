---
title: "How to Set Up AWS Cloud9 Environment"
datePublished: Sun Dec 18 2022 13:11:54 GMT+0000 (Coordinated Universal Time)
cuid: clbte0mpx000408jq7dmya6nx
slug: how-to-set-up-aws-cloud9-environment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671833582716/1871110b-bc8d-4c43-887b-5a301e6358f2.jpeg
tags: aws, ides, cloud9, eks, elastic-kubernetes-service

---

Cloud9 is a web-based IDE that runs on an AWS EC2 instance. This means we do not need to install any IDE on our local machine to be able to develop on AWS.

**Create Cloud9 Environment**

Navigate to the AWS console to create the environment. Click on Create environment. Fill in the detail which includes selecting the instance type.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671357667448/AUFTVZ0t4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671357905300/99Y08TjYP.png align="center")

Choose the default VPC under VPC settings

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671361317003/z4MVHghLN.png align="center")

Then click on Create. After the creation of cloud9, click on the name of the created cloud9 environment

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671363172363/hq_lJzG68.png align="center")

Click on Open in Cloud9

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671363375107/rJjx7zSaU.png align="center")

The Cloud9 IDE opens in another tab on your browser

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671363699114/_ScjZ7LgH.png align="center")

**Create An IAM Role for EC2**

We will then create an IAM role the EC2 instance which Cloud9 runs on will assume. This role will allow the EC2 instance to make API calls to other AWS services. Navigate to Identity and Access Management (IAM), under Acess Management, click Roles and then click Create role. Under the Trust entity type, select AWS services because the EC2 instance is an AWS service that will assume the role that is being created. Under the use case, select EC2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671365583039/lOls38tAP.png align="center")

Click next. To attach a policy to the role, search for and select AdministratorAccess from permissions policies and click next.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671366094655/kqCXy9iJi.png align="center")

Click next, name the role and create the role.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671366429521/hyPUOHLUA.png align="center")

Navigate to EC2 console, and click on instances to see the EC2 instance created on which cloud9 runs on.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671366973710/PUbfmzcmD.png align="center")

Select the EC2 instance, click the Actions dropdown menu, select Security and then select Modify IAM role. From the menu, select the role we created earlier and that click Update IAM role.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671367512607/dEOpzRzsc.png align="center")

**Remove The Temporary IAM Credentials for AWS Cloud9**

Go to AWS Cloud9 IDE, and choose Settings in the gear icon on the top right corner. Under Preferences, choose AWS settings and then choose Credentials. Turn off AWS managed temporary credentials and close the tab.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671368567162/SZ82s0sRH.png align="center")