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

The IAM role that publish vpc flow logs into Faro_Log_Group in CloudWatch Logs. The IAM role belong to **AWS account no :954976289682**

This policy allows AWS resources to publish VPC Flow Logs into Amazon CloudWatch Logs.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents",
        "logs:DescribeLogGroups",
        "logs:DescribeLogStreams"
      ],
      "Resource": "arn:aws:logs:us-east-1:954976289682:log-group:Faro-ec2-Logs:*"
    }
  ]
}

This trust policy allows the VPC Flow Logs service to assume the IAM role
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "vpc-flow-logs.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}


```


STEP 3.
Two Amazon EC2 instances  were created within the Faro_VPC to generate network traffic for
testing and validating VPC Flow Logs integration with Amazon CloudWatch Logs.



<img width="1887" height="753" alt="Two Faro EC2 Runing" src="https://github.com/user-attachments/assets/934b8d36-0cd2-4f70-ad07-f9054f9eaa0b" />




- Created  VPC named **Faro_VPC** to host the cloud networking environment.
- Launched two EC2 instances**Faro-EC2-(001)** and **Faro-EC2-(002)** within the VPC
  to simulate real network communication.
- Configured security groups to control inbound and outbound traffic between two EC2 instances.
- Network traffic was between EC2 instances using ping, SSH, and basic network tools.


STEP 4.

Launch EC2 instances.
- Connect via SSH.
- Ping www.google ,www.facebook.com , www.cnn.com  ,www.rccg.com
- from the Two EC2 Instances
- The enabled VPC Flow Logs **(VPC-Flow-Log-FARO)** captured all VPC network traffic.
- Configured Amazon CloudWatch Logs as the destination for flow log delivery.
- The CloudWatch Log Group named **Faro-ec2-Logs** stores and organized the log data.
- Attached an IAM role with required permissions to allow VPC Flow Logs to publish logs.
- Verified successful log ingestion by checking CloudWatch log streams.
- Observed and analyzed ACCEPT and REJECT network traffic events between EC2 instances.
- Used CloudWatch Logs Insights to query and analyze captured network traffic data.


<img width="1919" height="1059" alt="Network Interface for the two EC2" src="https://github.com/user-attachments/assets/7045392e-9ed9-41a0-a83e-ba9636abe0f1" />




 - **Interface ID** for the two EC2 Instances: Faro-EC2-(001) : **eni-03dfc15da123bd3d4**
    -    Faro-EC2-(002) : **eni-04acb2a0f6c5f371d**






Step 5: Verify Logs in CloudWatch
Open CloudWatch Console.
Navigate to Log Groups.
Open:
BeeQ-VPCFlowLogs
Review incoming flow log records.

Sample Log Entry:

Step 6: Analyze Traffic Patterns
<img width="1919" height="1060" alt="Network interface for the two EC2 (logs)" src="https://github.com/user-attachments/assets/fcf70973-78fe-4c34-8703-10789e4b4b17" />


AWS Cloudwatch Dashboard 

<img width="1907" height="980" alt="Cloud watch Summary" src="https://github.com/user-attachments/assets/a80c56df-b7f2-4f5a-acdc-9116ca5c1c3c" />



AWS Cloudwatch Dashboard 

<img width="1919" height="1041" alt="Cloudwatch Logs Dashboard 2" src="https://github.com/user-attachments/assets/a660b435-a81c-43ba-9e19-61ba2dddf6e1" />




**OPTION FOR STORING THE VPC FLOW LOGS**
 
-  Another way of options for storing VPC Flow Logs in Amazon S3 : Direct delivery to Amazon S3
-  VPC Flow Logs are sent directly to an S3 bucket and stored as compressed files. This is best for long-term storage, compliance, and cost-effective archiving.


-  CloudWatch Logs to S3 export:  Flow logs are first stored in CloudWatch Logs and then exported to an S3 bucket.
-  This is useful for real-time monitoring combined with long-term storage.






