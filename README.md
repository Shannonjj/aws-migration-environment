# AWS Migration Environment, Monitoring, and Outage Labs (CCA 625 / CCA 640)

A three-lab project series from my UMGC coursework: build a load-balanced web service on AWS, instrument it with a monitoring dashboard, then deliberately break it and watch the failure.

## Lab 1 — Build the AWS Migration Environment
- Stood up a web service behind an **Elastic Load Balancer** with an **Auto Scaling Group** and a custom **VPC**: two EC2 instances running **Nginx**, reachable at the load balancer's public DNS name
- Installed the EC2 **key pair** from the earlier project and launched instances **programmatically with Python** (`create_instance.py`) — the Cloud API portion of the project
- Connected to instances over **SSH** (PuTTY and PowerShell) and customized the **Nginx configuration**
- The build took four attempts (instance creation issues, then VPC issues) — the repetition is what made the load balancing / Auto Scaling concepts actually stick

## Lab 2 — Monitoring Dashboard
Built a CloudWatch dashboard for the environment tracking:
- **Load balancer**: Healthy Host Count, UnHealthy Host Count, Estimated ALB Active Connection Count, HTTP Code ELB 5XX, HTTP Code Backend 4XX, plus a latency bar graph
- **Auto Scaling Group / EC2**: CPU Utilization, Network In, Network Out

## Lab 3 — Site Outage Simulation
- Established baseline behavior on the dashboard, then simulated a **partial outage**, which evolved into a **complete outage** (Nginx service stopped)
- Observed healthy host count dropping to **0**, unhealthy hosts rising, and error/connection counts reacting — verifying that the monitoring detects failure and shows failover behavior between redundant systems

## Related work
- Prepared an **AWS Server Migration Service** configuration for a Hyper-V migration: IAM user with the **ServerMigrationConnector** and **ServerMigrationServiceRole** policies (CCA 640)
- Wrote the **Final Report to Executive Management** summarizing the project series

## Skills demonstrated
- Elastic Load Balancing, Auto Scaling Groups, EC2, VPC
- Python-driven instance provisioning; SSH administration; Nginx
- CloudWatch dashboard engineering and outage/failover observation


---
*Shannon Javone Jenkins — MS in Cloud Computing Architecture, University of Maryland Global Campus (UMGC). Graduate coursework and hands-on labs.*
