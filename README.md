# aws-security-lab

When it comes to security with cloud, systems must be protected and hardened so that important information won't be taken and compromised. 

# KMS Key
Go to KMS and on the left pane, choose Customer managed keys, then go and select create key and see these steps:    
![key](./images/key.png)    
Keep it on the symmetric option and encrypt and decrypt, then hit next and for Alias name have it be SecurityLab-S3-Key.    
But before going any further. go to IAM and create a user dedicated to kms-admin but clicking on create user and naming it kms-admin with the option to provide access to the command line, then hit next and select the option of attaching the AWS managed policy directly and choose AWSKeyManagementServicePowerUser, then review and click on create user and save the info provided. 

After naming the key, go to key admin permissions and select the kms-admin role that was just created and hit next until you see create and click on create to create or finish.

# S3 Bucket
Next go to S3 and click on create a bucket. For the first bucket name it jwt-security-lab-datav2 with public access blocked, enable bucket versioning, have encryption set to SSE-KMS or Server-Side Encryption, then for AWS KMS key select choose from existing and choose the one that was created and then have the bucket key enabled and hit create the first bucket. 
Then create a second bucket named jwt-security-lab-logs and leave it default and hit create. Then go to the security-lab-datav2 and go to properties, then scroll down to server access logging and hit edit. Change the server access logging from disable to enable and for the target bucket choose the lab-logs bucket and click on choose destination. Then in the destination after -logs add /s3-access-logs/ which should pop up for the Destination bucket name and destination prefix. Then click on save changes.    
![Server](./images/server.png)  

# CloudTrail
