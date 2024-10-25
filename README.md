![6244128f-414a-4707-84b3-3eaee6906241](https://github.com/user-attachments/assets/cd26a812-6bde-477b-83ac-cd2e92c8da5e)

# ✅Project OverView:
Automate deployment of a Node.js Application on Serverless AWS ECS fargate with the image repository on ECR and the cloudwatch integrated with proper IAM roles and configuration. 
1. In the Above Cover Image First, we will bring our application code from Github to the EC2 Instance of AWS. 
2. Now, We have to make a docker image of the Application and Push that on ECR(Elastic Container Registry) Services it is used to store docker images, so your EC2 instance must have access to ECR. 
3. To give access to ECR to EC2 Instance we will use IAM(Identity Access Management) service. We will give access of ECR full access, for that we have to create a user and make a policy for that. 
4. After Giving access we can push the docker image on ECR. and from there we can run our Image on ECS(Elastic Container Service) using Fargate. 
5. And from Cloudwatch we can access the logs of the Application.
##############################################################################################################################

# ✅Project Workflow:

![1702490266715](https://github.com/user-attachments/assets/041ab89f-db8f-43ff-9e32-3c5dd15a95f2)



✅ Steps:
# 1- First Create an EC2 instance on aws:
Using the AWS Management Console, create an EC2 instance where you'll clone the repository.
![ec2](https://github.com/user-attachments/assets/601849bc-27bf-42ab-8e8f-a2687d293287)


# 2- Cloning the Source Code from GitHub:

# 3- Install the AWS CLI and Docker onto EC2:

# 4 - Creating repository and pushing it onto ECR (Elastic Container Registry):

# ✅Creating Repository:

•	In the AWS Management Console, go to the "Services" drop down and select "ECR" under the "Container" section.

•	Click on the "Create repository" button.

•	Enter a unique repository name.

•	In content types select operating systems and architectures.

•	Click on the "Create repository" button.

•	Authenticate Docker to ECR:

•	In the ECR repository, click on the "View push commands" button.

•	Copy and paste the docker login command into your EC2 instance terminal to authenticate Docker to your ECR registry.

•	You need to create the IAM user with cli access for the secret key and password.

![ecs-ecr-repo](https://github.com/user-attachments/assets/6aebc7c7-7fe9-410d-a1fb-9c85d8536854)



# ✅Build, Tag and Push Docker Image:

•	Navigate to Your Project Directory:

•	Create a Dockerfile with the  application code.

•	Build your Docker image using the Dockerfile created.

•	Tag the Docker image with the ECR repository URI.

•	Push the Docker image to your ECR repository.

![docker-image-build](https://github.com/user-attachments/assets/ab1a246b-3b5a-4761-bebf-9364a5b52e2f)


•	Verify Image in ECR:

•	Go back to the ECR console and refresh the page.

•	You will see the pushed Docker image in the ecr repository.

![image-pushed-to-ecr](https://github.com/user-attachments/assets/6ba2f60e-ded9-4347-9836-389abf029e53)


# 5- Creating ECS cluster and task definition:
To create an Amazon ECS cluster with the necessary configuration, including a task definition and service, follow these steps:
1.	Navigate to ECS console:
•	In the AWS Management Console, go to the "Services" dropdown and select "ECS" under the "Compute" section.
2.	Create an ECS cluster:
•	Click on "Clusters" in the left sidebar. Click the "Create Cluster" button.
•	Choose a cluster template based on your needs. For example, you can start with the "EC2 Linux + Networking" template.
•	Configure the cluster settings:
•	Cluster Name: Enter a unique name for your ECS cluster.
•	Infrastructure type: AWS Fargate.
•	Monitoring : Use container insights.
![ecs-cluster-creating](https://github.com/user-attachments/assets/43b4ce17-167b-4bb0-b094-2cda8a028dcc)

![ecs-cluster](https://github.com/user-attachments/assets/56f9204b-fb7c-465c-9f37-d72b2c4ae1e7)



#	Create a Task Definition:
	
1.	In the ECS console, navigate to "Task Definitions" in the left sidebar.
2.	Click the "Create new Task Definition" button.
3.	Select the launch type compatibility (Fargate).
4.	Configure your task definition:
•	Task Definition Name: Enter a name for your task definition.
5.	Task Role: Choose the IAM role that provides permissions to your containers.
6.	Task Execution Role: Choose the IAM role for your task execution role.
7.	Define container definitions, image URL ( image URI from the ECR) , port mappings , environment variables, etc.

![task-def-creating](https://github.com/user-attachments/assets/1d974af7-d813-449d-a86f-23540fc18f50)

![task-def-creating1](https://github.com/user-attachments/assets/88e39f91-13a5-43a3-9883-375d5afddd2d)

![task-def-creating2](https://github.com/user-attachments/assets/6583cd30-fba1-4467-9416-970b5b9c5605)

![task-def-creating3](https://github.com/user-attachments/assets/ef2f07ca-ff53-49ca-bec8-0e8f7b76c505)

![enable-monitoring](https://github.com/user-attachments/assets/5c04b92b-c623-4d16-adad-b070ba823153)


![ecs-task-created](https://github.com/user-attachments/assets/7502b831-5a41-400c-bc4b-d742102d6be4)

# ✅Task Deployment: 
1. Review the details and create the task, followed by deployment and execution on the cluster using Fargate's automated management.
2. The task is now deployed to the cluster.
3. Open Port in the Security Group
4. Security Group Configuration: Navigate to the ENI ID associated with your task and access the corresponding security group.
5. Inbound Rule Modification: Open Port 80 (HTTP) in the inbound rule and restrict access to your IP for enhanced security.

![run-task](https://github.com/user-attachments/assets/ac2b3d45-18e9-48fe-a28a-1e0fd48bd9e5)

# ✅Project Live Execution
1.	Accessing Task Details: Navigate to the task created earlier and retrieve the public IP.
2.	Application Access: Access your live Node.js application using the provided Public IP address, witnessing your deployment in action.

![app-deployed](https://github.com/user-attachments/assets/edb0172c-0cd2-4dee-a19a-7e7430ed4729)

# ✅CloudWatch Monitoring:

![cloudwatch](https://github.com/user-attachments/assets/4e057354-8116-4318-9699-c66ec801932e)

# ✅Conclusion
successfully deployed a Node.js application on AWS ECS Fargate and ECR! 
















