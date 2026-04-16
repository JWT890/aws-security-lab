# aws-security-lab

When it comes to security with cloud, systems must be protected and hardened so that important information won't be taken and compromised. 

# KMS Key
Go to KMS and on the left pane, choose Customer managed keys, then go and select create key and see these steps:    
![key](./images/key.png)    
Keep it on the symmetric option and encrypt and decrypt, then hit next and for Alias name have it be SecurityLab-S3-Key.    
But before going any further. go to IAM and create a user dedicated to kms-admin but clicking on create user and naming it kms-admin with the option to provide access to the command line, then hit next and select the option of attaching the AWS managed policy directly and choose AWSKeyManagementServicePowerUser, then review and click on create user and save the info provided. 

After naming the key, go to key admin permissions and select the kms-admin role that was just created and hit next until you see create and click on create to create or finish.

Make sure to also for the kms-admin to have a policy that allows for CloudTrail to encrypt logs. So add this policy to the initial after clicking edit in permissions:  
![Policy](./images/trail.png)   

# S3 Bucket
Next go to S3 and click on create a bucket. For the first bucket name it jwt-security-lab-datav2 with public access blocked, enable bucket versioning, have encryption set to SSE-KMS or Server-Side Encryption, then for AWS KMS key select choose from existing and choose the one that was created and then have the bucket key enabled and hit create the first bucket. 
Then create a second bucket named jwt-security-lab-logs and leave it default and hit create. Then go to the security-lab-datav2 and go to properties, then scroll down to server access logging and hit edit. Change the server access logging from disable to enable and for the target bucket choose the lab-logs bucket and click on choose destination. Then in the destination after -logs add /s3-access-logs/ which should pop up for the Destination bucket name and destination prefix. Then click on save changes.    
![Server](./images/server.png)  

# CloudTrail
Then go to CloudTrail and click on create trail. Name the trail SecurityLab-Trail and hit create. After creation, double click on it and in general details click on edit and should be able to edit. For storage location, click on create a new S3 bucket and name it jwt-security-lab-cloudtrail. Then have enabled the Log File SSE-KMS encryption and for AWS KMS key have it existing and choose the S3 Security Lab alias. Then go and edit the CloudWatch logs and make sure that is disabled for logs. 
Then go to management events and click on edit and choose the read and write permissions or check to see if both are enabled

# IAM

# GuardDuty

# AWS Config