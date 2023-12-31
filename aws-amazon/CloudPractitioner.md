# AWS CERTIFIED CLOUD PRACTITIONER

### AWS Main Notes
###### Free Tier Information
- https://aws.amazon.com/free/compute/?p=ft&c=nhp&z=2&awswt=223

###### Connect to our EC2 Instances
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/session-manager.html


### Fundamentals of Cloud Computing Platform.
#### Data Center Approach
- Requirement: Your company wants to host their website.
- Solution: 
  * Choose the DataCenter/Hosting Provider
  * You need to typically send them enquiry about your requirements
  * They will contact you and price negociations.

Could computing is a model in which computing resources are available as a service. So we can customize based on our requiriments on a specific time.

Example 1:
Due to some big promotion, server capacity needs to be increased from 4GB RAM to 32GB RAM.

- Data Center Provider Way:
  * Buy a 32 GB RAM stick & install it onto your server.
- Hosting Provider Way:
  * Raise a support ticket and expect response within 15 minutes to 12 hours for response.
  * Get the DC guys to resize your server.
- Cloud Way:
  * Stop the server & change the instance size.

#### Cloud computing
Cloud computing is a model in which computing resource are available as a service.
- 3 important characteristic of Cloud Computing:
  * On-demand & self serviced \[Any time launch without manual intervention\]
  * Elasticity.               \[Can scale up and down anytime\]
  * Measured Service          \[Pay what you use\]

###### Types of cloud computing
There are 3 types of Cloud Computing models.
- Software as a service           \[Google Docs, Office 365\]
- Platform as a service           \[Google App Engine\]
- Infrastructure as a service     \[AWS, Linode, Digital Ocean\]

#### Architecture of Cloud Environments

###### Cloud is Data Center secretly
Cloud from behind the scenes is data center only.
Virtualization allows us to run multiple OS on a single hardware.
There are many virtualization softwares available like:
- VMware Workstation / vSphere
- KVM
- XEN
- VirtualBox

Now typically virtualization allows us to run multiple operating system on a single hardware.

#### On-Demand & Self Service
###### Challenges
- On-Demand does not always means that you will be able to launch instances at any given point of time.
- Event a Cloud provider has limits, though it might be high, these limits are definitely reached.

#### Elasticity
- Elasticity deals with adding and removing capacity, whenever it is needed in the environment.
- Capacity generally refers to mostly processing & memory.
- It is like a rubber band. 

#### Scalability
- Horizontal Scalability: Adding or removing instances from pool like cluster farm.
- Vertical Scalability: Adding or removing resource for existing servers.


### Core AWS Services.
#### Pay as you go Model
- Pay as you consume model allows organizations to scale their resources well and only pay for what they have used.
- Generally, the model works based on hourly costs.
- This model is terrific especially due to AWS Marketplace support.

#### AWS Global Infrastructure
###### Availability Zone
- AWS Data Centers are organized into Availability Zones (AZ)
- Each availability zone are located at lower-risk locations.
- There are multiple AZ and each of them is separate by geographic region.
- Each AZ is designed for independent failure zone.
- Thus, they are physically separated.
- The AZ are inter-connected with high speed private links.
- Each availability zone are located at lower-risk locations.

###### AWS Regions
- Each region contains two or more availability zones.
- AWS has 16 number of regions worldwide as of 2017.

###### AWS Global Infrastructure
- AWS currently operates on 16 regions across the world with 44 availability zones.

#### Setting up the lab
###### Create a free account
- Link: https://aws.amazon.com/free
- Add required information
- Fill out the required fields and choose Personal account.
- Once you finished the steps. You will receive a email.

#### Multi-Factor Authentication
- Go to your account's dropdown
- Choose My security credentials
- In the popup choose **Continue to security credentials**
- Go to **Multi-factor authentication (MFA)**
- Click on Activate MFA
- We will have some options, but for this example we will choose **Virtual MFA device**, since it is the simpler one.
- You will need to install Google Authenticator in your android device or as an chrome extension, then scan the QA code that will be generated.
- Assign the first two codes generated by the application
- That is it!
- After configure Multi-factor authentication, next time you will need to login, an MFA code will be required.

#### Creating our first IAM user
AWS Identity and Access Management is a service that allows you to control access to AWS resources (e.g. AWS EC2, S3, etc).

If someone gets your root account, he can do everything. However if someone gets far account of your name user, you can immediately restrict the access or block the access of the attacker. 

- Go to Services dropdown
- Choose IAM
- Go to users option
- Add user
- Fill required fields.
- Set the required permissions.
- Once done. The console will show you what is the link you require for accessing with the user.
- Then we can also configure the multi-factor authentication for this new user.

###### Important characteristics of IAM Users
- By default, a brand new IAM user does not have permissions to do any AWS operations or to access any AWS resources.
- IAM users allow you to assign permissions individually to each user.
- IAM users are not billed separately.
- AWS activity performed by users in your account is billed to your account.
- An IAM user does not have to be an actual person.
- Each an IAM user has its own security credentials (password & access key) to use AWS resources.

###### Important characteristics of IAM Groups
- IAM groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users.
- A group can contain many users, and a user can belong to multiple groups.
- Groups can not be nested; they can contain only users, not other groups.
- There is no default group that automatically includes all users in the AWS account. If you want to have a group like that, you need to create it and assign each new user to it.
- Default limit for groups in an AWS account is 300.

###### Important characteristics of IAM Policies
- Policy define permissions in aws.
- Policies are attached to IAM identities (identities = user, groups, or roles).
- Most users have multiple policies that together represent permissions for that user.
- Most policies in AWS are stored in JSON documents.

###### Main characteristics of Multi-Factor Authentication (MFA)
- MFA helps protect your AWS resources.
- MFA can be enabled for IAM users or the AWS root account.
- MFA adds extra security as it requires users to provide unique authentication from an AWS supported MFA mechanism.

###### Identity Federation
- Identity Federation is a mechanism which gives external users access to AWS resources
- It uses IAM identity providers (Amazon, Facebook, Google).
- Sample use case scenarios
  - If your organization already has its own identity system (eg. Microsoft Active Directory)
  - A web and mobile applications which require access to AWS resources.
- Why to use it?
  - External users do not need to have accounts in AWS
  - Improves security (you do not have to embed long-term credentials in your application)

###### IAM Best Practices
- Go to `docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html`

#### Setting up a billing alarm
- Go to your account name
- Choose `My Billing Dashboard`
- Go to `Billing preferences` menu
- It will show some options like `Receive free tier usage alerts` in `Cost Management Preferences` section.
- (As a initial case, we will not need to check `Receive Billing Alerts` because for that we need to setup budgets first)

-- --
###### Setting up a Billing Alarm
- Go to account name, then `Billing Dashboard`
- There are some approaches for setting up the billing alarm
- 1. **Budgets**: This service is not free, it costs like 2 cents per day.
- 2. **Free Tier Usage Alert**: Once we are alredy are in `Billing Dashboard`, we can go to:
- 2.1. Billing Preferences -> Check` Receive Free Tier Usage Alert`
- 3. In the same dashboard, we are going to see another check `Receive Billing Alerts`. However we will not need to check it because it uses the budgets.

#### Launching First EC2 Instance
- Go to Services or search in search field typing EC2.
- Choose EC2
- Go to instances
- Before launching an instance, first create a key pair
- Choose create key pair, and fill the fields. Basically this is going to be the private key.
- Then choose launch EC2 instance
- Choose a operating system
- Click on: Configure instance needed.
- Click on: Add storage
- Nex, next
- Security group configuration: Add a name
- Review and launch
- IN the modal choose, Select a key pair, and select the one created previously.
- Check the checkbox.
- Launch Instance.
- Click on the instance ID generated in the platform.
- We can connect through the public IP.
- With MobaXTerm. telnet ip
- In order to connect to the instance. We can do it via SSH
- ``` ssh ec2-user@ip ``` But it is going to fail asking the private key.
- Give the key some permissions. chmod 640 keyname.pem
- ``` ssh -i ~/path/keyname.pem ec2-user@ip ``` for fixing previous issue. Then you are going to be connected to your instance

###### Assign elastic IP address to our EC2 Instance
- Since the IP is not static, which means it changes every time we stop and relaunch our instances. So for avoiding it we can assign a elastic IP address.
- When the `elastic IP` is not assigned to any instance, then there will be costs associated to it.
- When the EC2 instance which has `elastic IP` associated to it is stopped, it will also cause costs.


###### Installing required tools into our EC2
- yum -y install nginx
- service nginx status
- If it is stopped: service nginx start
- netstat -ntlp
-  

###### Adding a new rule for connecting through a different ports
- Choose create security groups
- Inbound - Add a new rule
- Add the required values to the fields
- telnet ip port - It should work now.
- And accessing via a browser it should display a nginx page once it is installed.

###### Connecting to EC2 via Sesion Manager
- Some AMI does not have the required configurations for this feature, so we can use `Amazon Linux AMIs` since they has all the required configurations/software for allowing connection via Sesion Manager. This does not need SSH keys.
- For that we need to associate a `IAM Role` to the AMI instance.
  - Steps:
  - Select the instance
  - Go to `Actions` menu in the top
  - Hit `Security` menu
  - And choose `Modify IAM role`
  - The first time we do not have any IAM Role, so we will need to create one.
  - Select of trusted entity `AWS Service`
  - Choose an use case `EC2`
  - The new role has to have the following permissions: `AmazonSSMManagedInstanceCore`
  - Then complete the steps and saved it.
  - Once we have your IAM role, we can assign the role to our instance.
- After followed previous steps, when we go to the `connect` option and try to use `session manager`, we will still see a warning message like `We weren't able to connect your instance. Common reasons ....`
- That is because it takes some minutes to update the instances with IAM role. We can see it in `AWS Systems Manager` since `Sesion Manager` is part of it.
- Once it is ready, we can connect it with `Session Manager`.


###### Document - Installation Commands
Amazon has come up with the new Amazon Linux 2 OS.

If you are using Amazon Linux 2, the commands to install nginx will slightly change. Here are the new updated commands:

```bash
    amazon-linux-extras install nginx1.12
    systemctl start nginx
```

#### Understanding basics of firewall & TCP/IP
| Type          | Protocol      | Port Range  | Source       |
| ------------- |:-------------:|:-----------:|:------------:|
| SSH           | TCP           | 22          | 10.0.5.57/32 |

- Allow on port 22 only from the IP 10.0.5.57

Note:
> Wireshark is an appplication to capture the network traffic which includes the TCP/IP packages

#### Understanding basics of firewall & TCP/IP

###### NACL is Stateless
- Network ACL are stateless in nature.
- They operate at the subnet level instead of instance level like Security Groups
- All subnets in VPC must be associated with NACL.
- By default, Network ACL contains full allow in INBOUND and OUTBOUND.

###### Configuration
For configuring a ACL network perform the following steps:
- Go to Services.
- Type VPC in the search field.
- In the Filter by VPC field you are going to have options (it is going to appear one that was created when the instance was being created.)
- Scrolling down, you are going to see in Security section `Network ACLs`. Click on that option.

Within the option we are going to have Inbound Rules and Outbound Rules.
- In Rule# column, the lower the value, the more priority it has. (* means higher value)
- Example
  - Ping to the public IP, it is going to work
  - Now add a new rule, and DENY all traffic, after that ping should not work anymore.


#### Blok & object Storage Mechanism
###### Block Storage
- In block storage, the data is stored in terms of blocks
- Data stored in blocks are normally read or written entirely a whole block at the same time.
- Most of the file systems are based on block devices.

Examples of some commands to verify it.
- blockdev --getbsz /dev/sda
- lsblk

- Every block has an address and application can be called via SCSI call via it's address.
- There is no storage side meta-data associated with the block except the address.
- Thus block has no description, no owner.

#### Instance store volumes
AWS Instance Store provides a temporary block storage volumes for use with EC2.
This storage is located on the disks that are physically attached to the host computer.
Size of instance store varies depending on your instance type.

###### Steps:
- Going to Launch Instance
- Community AMIs
- We can see in Root device type section the option for instance store (temporary storage).
- Click in the option. It is going to be filtered all the images that support this feature.
- For this example we choose amzn-ami-minimal-pv-2016.03.1.x86_64-s3 - ami-008c056c
- Press select button
- It will show us multiple options, we will use the enabled ones but with option SMALL.
- Click on Configure Instance Details button.
- Click on Add Storage button.
- Leave all by default and press Review and Launch.
- Press launch.
- Select the required key.
- Launch Instance.
- Go to your instance.
- One thing to notice is that, if you scroll down, in the RootDeviceType option, you will see instance-store

###### Important Points for Instance Store.
- Data in instance store is lost in following situation.
  - The underlying disk drive fails.
  - The instance stops.
  - The instance terminates.
- Instance store are included in the cost of EC2 instance, so they are quite cost effective.
- If planning to use instance store, make sure you backup your data to central storage places like S3.

Connect to your Instance throught SSH. Then execute ```df -h```. You are going to see the following message ```/media/ephemeral10``` which means is a temporary device.
Something to realize is that you can not stop an instance-store instance, it only has reboot, and terminate options. It does not matter if you specifically executes a command for shutting it down, it will be terminated.

#### Elastic Block Store (EBS)
- AWS Elastic Block Store is a persistent block storage volumes for use with EC2.
- Each EBS volume is designed for 99.9999% availability & are automatically replicated within its availability zone.
- EBS can be elastic in nature, thus supports dynamic increase in capacity, performance and can change instance type of live volumes.

###### Compute != Storage
- AWS EC2 is regarded as compute based service.
- Compute generally refers to Memory & CPU

#### EBS Portability
- AWS Elastic Block Store is based on Network Attached Storage.
- Since the storage are attached via network, they can be easily detached as well hence providing the portability based feature.

Here some practical steps:
- Go to EC2 Dashboard.
- Go to Elastic Block Store section and click Volumes menu.
- Create volume and fill all the fields.
- It is recommended to have the AvailabilityZone the same as the instance that is being executed. So if you are connected in different availability zone then it will not work.
- Create Volume, it will show us available state, so it is ready for attach to a EC2 instance.
- Rename it to portable.

You will need your EC2 instance running, and then connect to it for applying the following operations
- ssh -i keypair.pem ec2-user@public-ip
- sudo su -
- lsblk : we will see all the volumes.
- Now we can attach the previous volume created to this instance.
- When we are in volume dashboar, click on actions -> Attach Volume -> choose the instance 
- Once performed previous operations, you should able to see the new volume in you block devices section.
- lsblk
- For creating a file system into the volume created: mkfs.ext4 /dev/xvdf (which is the volume that has been attached)
- mkdir /somefolder
- mount /dev/xvdf /somefolder
- cd somefolder
- touch somefolder.txt
- echo "This is EBS Portability lecture" > somefolder.txt
- cat somefolder.txt
- cd ..
- umount /somefolder
- df -h 
- We can also detach throught the UI with detach option, and then from IN USE, in will change to AVAILABLE state, then you can use it in a different instance.






































