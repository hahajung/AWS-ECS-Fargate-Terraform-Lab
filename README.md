This is my second lab on AWS using Terraform!

Through this lab, my goal is to
1. Implement ECS Fargate Apps on AWS using Terraform with IaC
2. Create an SSL HTTPS certificate for Route53 doamin
3. Launch infrastructure on AWS without even signinig in on AWS
4. Learn how to work with AWS Fargate using Terraform
5. Learn to register a domain with Route53 and use with application load balancer for AWS ECS Fargate
6. Learn to implement 3-layered production-grade infrastructure on AWS using Terraform IaC

I started by implementing remote state and obataining key pair which is used to connect to the instances I launch. Then I created VPC environment. To increase the high-availability, I spread the private and public subnets to three different availability zones inside a region. I also created private and public route tables to manage the routing between resources inside VPC.

IGW is attach to the VPC to use with public subnets so the resources int hose will be able to access and receive public internet traffic. The private subnet needs some form of internet but not both ways. Hence, NAT gateway is launched and attached to the private route table.

I registered a domain which will be used for the demo spring boot applicaation. First I crated ECS Cluster, target group, application load blanacer, https listener and certificate and IAM roles for ecs cluster.

Then I implemented ECS fargate task definintion along with creating IAM role and Policy, ECS Service, target group, lisener rule and cloudwatch log group.

Next, I scripted the whole pipeline of the appplication from building with Maven to pushing docker image to AWS ECR and to deploy to AWS ECS Fargate. I created a shell-script to implment everything as different stage and develop the whole pipeline.

Once finished with pipeline, I began building the code, building and pushing docker image to AWS ECR and finally deploy spring boot application to AWS ECR Fargate to have it up and running in the registered domain.
