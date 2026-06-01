# AWS-Network-Traffic-Monitoring-Using-VPC-Flow-Logs-and-CloudWatch-Logs
(Monitoring VPC Flow Logs in Amazon CloudWatch Log Groups to Analyze Network Traffic and Enhance Security Visibility)
<img width="1" height="1" alt="image" src="https://github.com/user-attachments/assets/60902527-bcce-425d-bd07-97f6728f3c1f" />
This project demonstrates how to enable and monitor VPC Flow Logs within an 
AWS environment(Network) and send them to Amazon CloudWatch Log Groups for centralized 
visibility and analysis. It provides insight into network traffic flowing in 
and out of VPC resources, helping to identify security threats, troubleshoot
connectivity issues, and improve overall network performance.
Key components include configuring VPC Flow Logs, integrating with CloudWatch
Logs, and analyzing traffic patterns for security monitoring and operational 
insights within an AWS VPC architecture.
             
  Reference Architecture 
             
<img width="1" height="1" alt="image" src="https://github.com/user-attachments/assets/60902527-bcce-425d-bd07-97f6728f3c1f" />
<img width="651" height="422" alt="vpc flow log" src="https://github.com/user-attachments/assets/d04ce98c-fc66-4705-afc5-48a6f49dde6a" />



VPC Flow Logs capture information about the IP network traffic going to and 
from network interfaces in your VPC. They help you monitor, troubleshoot, and 
audit network activity within your AWS environment.
A flow log can capture information such as:
•	Source IP address 
•	Destination IP address 
•	Source port 
•	Destination port 
•	Protocol (TCP, UDP, ICMP) 
•	Number of packets transferred 
•	Bytes transferred 
•	Traffic acceptance or rejection (ACCEPT or REJECT)
<img width="1" height="1" alt="image" src="https://github.com/user-attachments/assets/cfd85cb5-8020-4465-89d7-66ee7c5cb68c" />


