



# Highly Available Web Application using Auto Scaling & Application Load Balancer

## 🌐 Project Overview

This project demonstrates how to build a highly available and scalable web application on AWS using Application Load Balancer (ALB) and Auto Scaling. The setup ensures that the application remains accessible even during high traffic or instance failure.

The system distributes incoming traffic across multiple EC2 instances using a load balancer, while Auto Scaling dynamically adjusts the number of instances based on demand. This improves reliability, fault tolerance, and overall performance of the application.

---

## ✨ Key Highlights

- Designed a fault-tolerant web architecture on AWS  
- Traffic distribution using Application Load Balancer  
- Automatic scaling based on demand  
- High availability with multiple EC2 instances  
- Continuous health monitoring of instances  

---
 

## 🏗️ Architecture Overview

The application is designed using a distributed architecture where incoming traffic is managed efficiently using an Application Load Balancer. Multiple EC2 instances are deployed to ensure high availability and fault tolerance.

Auto Scaling dynamically adjusts the number of instances based on user demand, ensuring optimal performance and cost efficiency.

![Architecture Diagram](https://github.com/Manishakhatri23/Highly_available_web_application/blob/main/Image/Architecture_diagram.png)

---

## 🔄 How It Works

- User requests are received by the Load Balancer  
- The Load Balancer distributes traffic across EC2 instances  
- Auto Scaling increases or decreases instances based on load  
- Health checks ensure only healthy instances serve traffic  

---

## 📂 Project Structure

```bash
Highly_available_web_application/
|
│── README.md
│── index.html
| 
│── Image/    
|   ├── Architecture_diagram.png 
|  
│── Screenshots/    
|   ├── ALB_DNS_output.png  
|   ├── ALB_configuration.png  
|   ├── ASG_Configuration.png  
|   ├── Auto_scaling_events.png  
|   ├── Load_testing.png  
|   ├── Target_group_health_check.png                   

```

---

## 🛠️ AWS Services Used

| AWS Service | Purpose |
|------------|--------|
| Amazon EC2 | Virtual servers used to run the web application |
| Amazon VPC | Provides isolated and secure network environment |
| Launch Template | Defines instance configuration including user data |
| Auto Scaling Group | Automatically launches and replaces EC2 instances |
| Application Load Balancer | Distributes incoming traffic across instances |
| Amazon CloudWatch | Monitors instance health and triggers scaling actions | 

---

## ⚙️ Implementation Steps
### 1️⃣ Networking Configuration 

- Custom VPC created with defined CIDR block  
- Two public subnets configured  
- Subnets distributed across multiple Availability Zones  
- Internet Gateway attached
- Configured Route Tables

---

### 2️⃣ Launch Template  
A Launch Template is created to standardize EC2 configuration across all instances.

#### Includes:
- AMI  
- Instance Type  
- Security Groups  

#### Automation:
- Installs web server  
- Deploys application automatically  

---

### 3️⃣ Create Auto Scaling Group 
#### Auto scaling group configuration:
- Minimum Instances → 2  
- Maximum Instances → 5  
- Desired Capacity → 2   
- Scaling policy: Target tracking based on CPU utilization  
 
---

### 4️⃣ Create Application Load Balancer
#### Application Load Balancer Configuration:

An Application Load Balancer (ALB) is used to distribute incoming traffic across multiple instances.
Features:
- Accepts HTTP requests  
- Distributes traffic evenly  
- Connected to ASG via Target Group  
- Performs continuous health checks

---

### 5️⃣ Failover Testing

To validate the fault tolerance of the system, a failover test was performed by manually terminating one of the running EC2 instances.

⚙️ Automatic Recovery:

- ASG automatically launched a new EC2 instance using the launch template
- The new instance was configured and brought into service without manual intervention
- Once healthy, it was automatically added back to the load balancer

Result:
The application continued to serve users without interruption, demonstrating high availability and zero downtime capability

---

### 6️⃣ Scaling Validation
Generated load using stress tool / traffic

#### Observation:
  - New instances launched automatically
  - Load distributed across instances

Captured scaling events in CloudWatch


---

## 📊 Monitoring
Application performance is monitored using Amazon CloudWatch. Metrics Observed:

- CPU Utilization
- Auto Scaling events
- Instance health


---

## 🔐 High Availability Strategy Explained

- Multi-AZ Deployment → Ensures availability even if one AZ fails  
- Load Balancer → Eliminates single point of failure  
- Auto Scaling → Maintains required number of instances  
- Health Checks → Routes traffic only to healthy instances 

---

## 📊 Results & Observations
✅ Application remained live during failure  
✅ Traffic handled efficiently under load  
✅ Instances scaled dynamically  
✅ No manual intervention required 

---

## 📸 Output Screenshots

### 1 Application Load Balancer Configuration
![ALB_config](https://github.com/Manishakhatri23/Highly_available_web_application/blob/main/Screenshots/ALB_configuration.png)

### 2 Application Load Balancer Output
![ALB_output](https://github.com/Manishakhatri23/Highly_available_web_application/blob/main/Screenshots/ALB_DNS_output.png)

### 3 Target Group Health Check
![TG_health_check](https://github.com/Manishakhatri23/Highly_available_web_application/blob/main/Screenshots/Target_group_health_check.png)

### 4 Auto Scaling Group Configuration
![ASG_config](https://github.com/Manishakhatri23/Highly_available_web_application/blob/main/Screenshots/ASG_Configuration.png)

### 5 Auto Scaling Events
![Auto_scaling_event](https://github.com/Manishakhatri23/Highly_available_web_application/blob/main/Screenshots/Auto_scaling_events.png)

### 6 Load testing
![Load_testing](https://github.com/Manishakhatri23/Highly_available_web_application/blob/main/Screenshots/Load_testing.png)

---

## 📌 Conclusion
This project successfully demonstrates how to build a highly available and scalable web application architecture on AWS. By using EC2, Auto Scaling Group, and Application Load Balancer, the system can automatically handle traffic spikes and maintain application availability. The architecture distributes traffic across multiple instances in different Availability Zones and automatically replaces unhealthy instances, ensuring reliability and eliminating single points of failure.

---
## 👩‍💻 Author

**Manisha Khatri**

🔗 GitHub: https://github.com/Manishakhatri23
