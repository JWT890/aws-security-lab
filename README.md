# aws-security-lab

When it comes to security with cloud, systems must be protected and hardened so that important information won't be taken and compromised. 

# KMS Key
Go to KMS and on the left pane, choose Customer managed keys, then go and select create key and see these steps:    
![key](./images/key.png)    
Keep it on the symmetric option and encrypt and decrypt, then hit next and for Alias name have it be SecurityLab-S3-Key.    
But before going any further. go to IAM and create a user dedicated to kms-admin but clicking on create user and naming it kms-admin with the option to provide access to the command line, then hit next and select the option of attaching the AWS managed policy directly and choose AWSKeyManagementServicePowerUser, then review and click on create user and save the info provided. 

After naming the key, go to key admin permissions and select the kms-admin role that was just created and hit next until you see create and click on create to create or finish.

# S3 Bucket