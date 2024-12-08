# Node.js AWS Infrastructure
![architecture diagram](https://github.com/user-attachments/assets/1953c21e-6566-4c62-812e-6cde4e3e9109)

## Solution Overview
This solution utilizes AWS services for a secure, scalable, and cost-efficient cloud architecture, with **Terraform** for infrastructure automation and **GitHub Actions** for deployment.

## AWS Architecture

1. **Virtual Private Cloud (VPC)**  
   The VPC is configured to isolate resources securely, offering precise control over traffic flow. It includes:  
   - **Two public subnets** for ECS tasks and the Application Load Balancer (ALB).  
   - **Two private subnets** for the RDS instance.  
   - All resources are distributed across **two availability zones** to ensure high availability and fault tolerance.

2. **Elastic Container Service (ECS) with Fargate**  
   ECS with Fargate simplifies container orchestration, providing a serverless environment for containerized application deployment. This eliminates the need to manage EC2 instances and allows for dynamic scaling based on CPU and memory utilization. ECS tasks pull Docker images from **Amazon ECR** and run in public subnets with auto-scaling policies for optimal performance.

3. **Application Load Balancer (ALB)**  
   The ALB ensures high availability by distributing incoming traffic across ECS tasks. It enhances fault tolerance and allows seamless handling of varying traffic loads, using target groups and listeners to forward HTTP requests to ECS tasks.

4. **Relational Database Service (RDS)**  
   **PostgreSQL** is deployed in private subnets to ensure security by isolating the database from public access. RDS is a managed solution, reducing operational overhead with automated backups, scaling, and maintenance.

5. **Security Groups and IAM Roles**  
   - **Security Groups** restrict inbound and outbound traffic for ECS, RDS, and ALB, enhancing security.  
   - **IAM Roles** enforce the principle of least privilege by assigning only the necessary permissions to ECS tasks and Terraform for secure interactions with AWS services.

## Getting Started
1. Clone this repository.
2. Configure AWS credentials using Terraform.
3. Deploy infrastructure using Terraform scripts.
4. Automate deployments with GitHub Actions.

---

This setup provides a robust, secure, and scalable cloud infrastructure for containerized Node.js applications.
