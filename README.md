# AWS-Network-Traffic-Monitoring-Using-VPC-Flow-Logs-and-CloudWatch-Logs
(Monitoring VPC Flow Logs in Amazon CloudWatch Log Groups to Analyze Network Traffic and Enhance Security Visibility)
<img width="1" height="1" alt="image" src="https://github.com/user-attachments/assets/60902527-bcce-425d-bd07-97f6728f3c1f" />

This project demonstrates how to monitor network traffic within an AWS VPC by 
enabling VPC Flow Logs and publishing them to CloudWatch Logs for analysis, 
troubleshooting, and security monitoring.It provides insight into network
traffic flowing in and out of VPC resources, helping to identify security 
threats, troubleshoot connectivity issues, and improve overall network performance.
Key components include configuring VPC Flow Logs, integrating with CloudWatch
Logs, and analyzing traffic patterns for security monitoring and operational 
insights within an AWS VPC architecture.
             
  Reference Architecture 
             
<img width="1" height="1" alt="image" src="https://github.com/user-attachments/assets/60902527-bcce-425d-bd07-97f6728f3c1f" />
<img width="651" height="422" alt="vpc flow log" src="https://github.com/user-attachments/assets/d04ce98c-fc66-4705-afc5-48a6f49dde6a" />


VPC Flow Logs Capture the Following Information
Source IP Address – Identifies the origin of the network traffic.
Destination IP Address – Identifies the target of the network traffic.
Source Port – Shows the port number used by the originating application or service.
Destination Port – Indicates the port number on the receiving application or service.
Protocol – Records the network protocol in use, such as:
TCP
UDP
ICMP
Packet Count – Displays the total number of packets transferred during the connection.
Bytes Transferred – Measures the amount of data exchanged between the source and destination.
Traffic Action – Indicates whether the traffic was:
ACCEPT – Traffic was allowed by the network configuration.
REJECT – Traffic was denied by the network configuration.

This format is concise, professional, and well-suited for GitHub project documentation.





A flow log can capture information such as:
•	Source IP address 
•	Destination IP address 
•	Source port 
•	Destination port 
•	Protocol (TCP, UDP, ICMP) 
•	Number of packets transferred 
•	Bytes transferred 
•	Traffic acceptance or rejection (ACCEPT or REJECT)

STEP.
<img width="1" height="1" alt="image" src="https://github.com/user-attachments/assets/cfd85cb5-8020-4465-89d7-66ee7c5cb68c" />

<img width="1687" height="653" alt="Two Faro EC2 Runing" src="https://github.com/user-attachments/assets/2f64d170-c67b-4abf-b176-5af3c98b4977" />

This project demonstrates how to monitor network traffic within an AWS VPC by enabling VPC Flow Logs and publishing them to CloudWatch Logs for analysis, troubleshooting, and security monitoring.

Architecture
Amazon VPC
Public and Private Subnets
EC2 Instances
VPC Flow Logs
CloudWatch Log Group





IAM Role and Policy
Step 1: Create a CloudWatch Log Group
Navigate to CloudWatch Console.
Select Logs → Log Groups.
Click Create Log Group.
Enter a name:
BeeQ-VPCFlowLogs
Click Create.

Step 2: Create an IAM Role for VPC Flow Logs
Navigate to IAM Console.
Select Roles → Create Role.
Choose:
AWS Service
VPC Flow Logs
Attach permissions to allow publishing logs to CloudWatch.
Name the role:
BeeQ-VPCFlowLogs-Role
Create the role.






Step 3: Create the VPC Flow Log
Navigate to VPC Dashboard.
Select Your VPCs.
Choose the target VPC:
BeeQVPC
Select Flow Logs tab.
Click Create Flow Log.

Configure:

Setting	Value
Filter	All
Destination	Send to CloudWatch Logs
Log Group	BeeQ-VPCFlowLogs
IAM Role	BeeQ-VPCFlowLogs-Role
Traffic Type	All
Click Create Flow Log.
Step 4: Generate Network Traffic

To generate log entries:

Launch EC2 instances.
Connect via SSH.
Ping www.google ,www.facebook.com , www.cnn.com  ,www.rccg.com
from the Two Ec2 Instances.
<img width="1887" height="753" alt="Two Faro EC2 Runing" src="https://github.com/user-attachments/assets/f5703435-bc54-46e3-8d51-7ed2f864ff1a" />


Access websites from the instances.
Perform ping and network connectivity tests.
Generate inbound and outbound traffic.
Step 5: Verify Logs in CloudWatch
Open CloudWatch Console.
Navigate to Log Groups.
Open:
BeeQ-VPCFlowLogs
Review incoming flow log records.

Sample Log Entry:

2 123456789012 eni-1234567890abcdef 10.0.1.10 8.8.8.8 443 52344 6 10 840 1717000000 1717000060 ACCEPT OK
Step 6: Analyze Traffic Patterns
<img width="1919" height="1060" alt="Network interface for the two EC2 (logs)" src="https://github.com/user-attachments/assets/fcf70973-78fe-4c34-8703-10789e4b4b17" />

Review:

Accepted connections
Rejected connections
Source and destination IP addresses
Protocols used
Port activity
Traffic volume
Step 7: Create CloudWatch Metric Filters
Open CloudWatch.
Navigate to:
Logs → Log Groups
Select:
BeeQ-VPCFlowLogs
Create Metric Filters for:
REJECT traffic
SSH activity (Port 22)
RDP activity (Port 3389)
Step 8: Create CloudWatch Alarms

Create alarms to notify administrators when:

Excessive rejected traffic occurs.
Unusual network activity is detected.
Traffic exceeds predefined thresholds.
Step 9: (Optional) Archive Logs to Amazon S3

For long-term retention:

Create an S3 bucket.
Configure Flow Logs to deliver logs to S3.
Enable lifecycle policies for cost optimization.
Project Outcomes
Improved network visibility.
Enhanced security monitoring.
Faster troubleshooting of connectivity issues.
Centralized log management using CloudWatch.
Audit-ready network traffic records.
AWS Services Used
Amazon VPC
Amazon EC2
Amazon CloudWatch Logs
AWS Identity and Access Management (IAM)
Amazon S3 (Optional)
VPC Flow Logs

