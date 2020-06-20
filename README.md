# AWS-Ec2-Instance
AWS-Ec2-Instance


#Some of the important pre-requisites before we launch an EC2 instance on AWS are as below

1.)Key Pair

2.)Security Groups

3.)Inbound/Outbound Rules for Security groups

We can do the above steps using the AWS UI or by using AWS CLI.

We install the AWS Cli and then execute the AWS cli commands

we check the existing key pairs using 

aws ec2 describe-key-pairs

We crate the key pairs using the below command:

aws ec2 create-key-pair --key-name 'keypairfile.pem' --query 'KeyMaterial' --output text > keypairfile.pem

For creating the Security group from the command line we need to get the VPC id.

aws ec2 describe-vpcs

We create the security groups from below command

aws ec2 create-security-group vpcId 

C:\Users\Dhana Shekhar>aws ec2 create-security-group --group-name first-sg --des
cription "first security group" --vpc-id vpcId

aws ecc2 describe--security-groups

aws ec2 authorize-security-group-ingress --group-id sg-02e9dbae9eb8955f7 --protocol tcp --port 22 --cidr 157.48.200.162/32

Get your public ip address from below URL
http://checkip.amazonaws.com/
    
   
  Let us find the AMI id to launch the Ec2 instance.
  
  Check if any existing EC2 instances.
  
  aws ec2 describe-instances
  
C:\Users\Dhana Shekhar>aws ec2 describe-instances
{
    "Reservations": []
}

vpcid
vpc-40aa4c3dvpc-40aa4c3d
subnetid:
subnet-bd8f45db - 


We have by defaut the subnets created in eachof the availability zones.
aws ec2 run-instances --image-id amiid --count 1 --instance-type t2.micro --key-name 'kpair' --security-group-ids sgid --subnet-id sbntid


Issues into:

First the ec2 isntance was unable to get created.

The default subnets were 6 in number and the subnet id i have selected was the last one .

I had to choose the correct subnet id based on the Region my user account is available in.

Connection timed out issue while doing ssh:

The issue was wit the inbound rules in the associated security group for the ec2 instance.

Eventhough I got the ip address from the http://checkip.amazonaws.com/ and put the same while creating the security groups using command line, the inbound rules source when updated to My Ip worked

The next issue which I ran into was the pem file being complained as in invalid format.

When opened in note pad the pem file was badly downloaded.

C:\Users\Dhana Shekhar>aws ec2 create-key-pair --key-name first-keypair --quer
y KeyMaterial --output text > first-keypair.pem
 
 
 
 


  
  
  
    


