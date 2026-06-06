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


## 📊 VPC Flow Logs Capture the Following Information

- **Source IP Address** – The origin of the network traffic.
- **Destination IP Address** – The target of the network traffic.
- **Source Port** – The port used by the source application.
- **Destination Port** – The port used by the destination application.
- **Protocol** – The network protocol (TCP, UDP, or ICMP).
- **Packet Count** – The total number of packets transmitted.
- **Bytes Transferred** – The total volume of data exchanged.
- **Traffic Action** – Indicates whether the traffic was **ACCEPTED** or **REJECTED** by the VPC.


STEP 1.
Create an Amazon CloudWatch Log Group named **Faro-ec2-Logs** to serve as the destination 
for VPC Flow Logs. Configure the VPC Flow Log **VPC-Flow-Log-FARO** for **Faro_VPC** to 
publish its network traffic logs to this CloudWatch Log Group for centralized monitoring 
and analysis.

<img width="1893" height="919" alt="vpc-logs drom faro" src="https://github.com/user-attachments/assets/00967a84-2883-4023-9ac2-9d0a45be7cdd" />


STEP 2.
After creating CloudWatch Log Group and configuring the VPC Flow Log,the next steps are:
The IAM policy provides the permissions required for Amazon VPC Flow Logs to publish logs
to Amazon CloudWatch Logs.

-Create an IAM role that allows VPC Flow Logs to publish logs to CloudWatch.









STEP 3.
Two Amazon EC2 instances  were created within the Faro_VPC to generate network traffic for
testing and validating VPC Flow Logs integration with Amazon CloudWatch Logs.




- Created a VPC named **Faro_VPC** to host the cloud networking environment.
- Launched two EC2 instances**Faro-EC2-(001)** and **Faro-EC2-(002)** within the VPC
  to simulate real network communication.
- Configured security groups to control inbound and outbound traffic between two EC2 instances.
- Network traffic was between EC2 instances using ping, SSH, and basic network tools.


STEP 4.

Launch EC2 instances.
- Connect via SSH.
- Ping www.google ,www.facebook.com , www.cnn.com  ,www.rccg.com
- from the Two EC2 Instances

<img width="1887" height="753" alt="Two Faro EC2 Runing" src="https://github.com/user-attachments/assets/f5703435-bc54-46e3-8d51-7ed2f864ff1a" />


- The enabled VPC Flow Logs **(VPC-Flow-Log-FARO)** captured all VPC network traffic.
- Configured Amazon CloudWatch Logs as the destination for flow log delivery.
- The CloudWatch Log Group named **Faro-ec2-Logs** stores and organized the log data.
- Attached an IAM role with required permissions to allow VPC Flow Logs to publish logs.
- Verified successful log ingestion by checking CloudWatch log streams.
- Observed and analyzed ACCEPT and REJECT network traffic events between EC2 instances.
- Used CloudWatch Logs Insights to query and analyze captured network traffic data.


 - **Interface ID** for the two EC2 Instances: Faro-EC2-(001) : **eni-03dfc15da123bd3d4**
    -    Faro-EC2-(002) : **eni-04acb2a0f6c5f371d**


<img width="1919" height="1059" alt="Network Interface for the two EC2" src="https://github.com/user-attachments/assets/7045392e-9ed9-41a0-a83e-ba9636abe0f1" />




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

