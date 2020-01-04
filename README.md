# CloudFormation to provision Amazon ECS Clsuter and deploy helloworld web app service

This CloudFormation templates provision an ECS cluster (including all components like: task definition, service, load balancer, target group, launch configuration ...etc), then deploy the helloworld web app service, creating the Auto Scaling Group, and create an ELB in front of the service. 

## Below are the main resources provisioned via the template:

 - ECS Cluster
 - ECS Security group that allows inbound traffic from ports: TCP 80, 22, and TCP range from (31000 to 61000).
 - Task definition with 2 container definitions: Apache and busybox images.
 - The applicaion load balancer and its listner.
 - The target group which depends on the ELB and has port 80.
 - An auto scaling group with min capacity of 2 and desired capacity as defined in parameters section.
 - The ECS Service that depend on the ECS task definition, ALB, and the target group.
 - The IAM role to give EC2 Instances thePermissions to talk to an ECS Cluster.
 - CloudWatch logs.

During the stack creation wizard, you specify the stack name, desired capacity , maximum capacity (4
instances), the EC2 instance type (default is: t2.micro), the 2 subnets that are in 2 different AZs, the VPC network.

The ***outputs*** tab has the ELB name, ECS Cluster name, the ARNs of the ECS Service and task definition  