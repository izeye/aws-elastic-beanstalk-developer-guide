# Configuring EC2 Server Instances Using AWS Toolkit for Eclipse<a name="create_deploy_Java.managingappenv.ec2"></a>

Amazon Elastic Compute Cloud \(EC2\) is a web service for launching and managing server instances in Amazon's data centers\. You can use Amazon EC2 server instances at any time, for as long as you need, and for any legal purpose\. Instances are available in different sizes and configurations\. For more information, go to the [Amazon EC2 product page](https://aws.amazon.com/ec2/)\.

 Under **Server**, on your environment's **Configuration** tab inside the Toolkit for Eclipse, you can edit the Elastic Beanstalk environment's Amazon EC2 instance configuration\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/aeb-eclipse-server-config.png)

## Amazon EC2 Instance Types<a name="create_deploy_Java.managingappenv.ec2.instancetypes"></a>

**Instance type** displays the instance types available to your Elastic Beanstalk application\. Change the instance type to select a server with the characteristics \(including memory size and CPU power\) that are most appropriate to your application\. For example, applications with intensive and long\-running operations can require more CPU or memory\.

For more information about the Amazon EC2 instance types available for your Elastic Beanstalk application, see [Instance Types](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html) in the *Amazon Elastic Compute Cloud User Guide*\.

## Amazon EC2 Security Groups<a name="create_deploy_Java.managingappenv.ec2.securitygroups"></a>

You can control access to your Elastic Beanstalk application using an *Amazon EC2 Security Group*\. A security group defines firewall rules for your instances\. These rules specify which ingress \(i\.e\., incoming\) network traffic should be delivered to your instance\. All other ingress traffic will be discarded\. You can modify rules for a group at any time\. The new rules are automatically enforced for all running instances and instances launched in the future\. 

You can set up your Amazon EC2 security groups using the AWS Management Console or by using the AWS Toolkit for Eclipse\. You can specify which Amazon EC2 security groups control access to your Elastic Beanstalk application by entering the names of one or more Amazon EC2 security group names \(delimited by commas\) into the **EC2 Security Groups** box\. 

**Note**  
If you are running your application using a legacy container type, make sure port 80 \(HTTP\) is accessible from 0\.0\.0\.0/0 as the source CIDR range if you want to enable health checks for your application\. For more information about health checks, see [Health Checks](create_deploy_Java.managingappenv.elb.md#create_deploy_Java.managingappenv.elb.healthchecks)\. To check if you are using a legacy container type, see [Why are some container types marked legacy?](using-features.migration.md#using-features.migration.why)\.

**To create a security group using the AWS Toolkit for Eclipse**

1. In the AWS Toolkit for Eclipse, click **AWS Explorer** tab\. Expand the **Amazon EC2** node, and then double\-click **Security Groups**\. 

1. Right\-click anywhere in the left table, and then click **New Group**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/aeb-eclipse-security-group.png)

1. In the **Security Group** dialog box, type the security group name and description and then click **OK**\. 

For more information on Amazon EC2 Security Groups, see [Using Security Groups](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html) in the *Amazon Elastic Compute Cloud User Guide*\.

## Amazon EC2 Key Pairs<a name="create_deploy_Java.managingappenv.ec2.keypair"></a>

You can securely log in to the Amazon EC2 instances provisioned for your Elastic Beanstalk application with an Amazon EC2 key pair\.

**Important**  
You must create an Amazon EC2 key pair and configure your Elastic Beanstalk\-provisioned Amazon EC2 instances to use the Amazon EC2 key pair before you can access your Elastic Beanstalk\-provisioned Amazon EC2 instances\. You can create your key pair using the **Publish to Beanstalk Wizard** inside AWS Toolkit for Eclipse when you deploy your application to Elastic Beanstalk\. Alternatively, you can set up your Amazon EC2 key pairs using the [AWS Management Console](https://console.aws.amazon.com/)\. For instructions on creating a key pair for Amazon EC2, see the [Amazon Elastic Compute Cloud Getting Started Guide](http://docs.aws.amazon.com/AWSEC2/latest/GettingStartedGuide/)\. 

For more information on Amazon EC2 key pairs, go to [Using Amazon EC2 Credentials](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-credentials.html) in the *Amazon Elastic Compute Cloud User Guide*\. For more information on connecting to Amazon EC2 instances, go to [Connecting to Instances](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstances.html) and [ Connecting to a Linux/UNIX Instance from Windows using PuTTY ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html) in the *Amazon Elastic Compute Cloud User Guide*\. 

## CloudWatch Metrics<a name="create_deploy_Java.managingappenv.monitoring"></a>

 By default, only basic Amazon CloudWatch metrics are enabled\. They return data in five\-minute periods\. You can enable more granular one\-minute CloudWatch metrics by selecting **1 minute** for the **Monitoring Interval** in the **Server** section of the **Configuration** tab for your environment in the AWS Toolkit for Eclipse\.

**Note**  
Amazon CloudWatch service charges can apply for one\-minute interval metrics\. See [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) for more information\.

## Custom AMI ID<a name="create_deploy_Java.managing.customami"></a>

 You can override the default AMI used for your Amazon EC2 instances with your own custom AMI by entering the identifier of your custom AMI into the **Custom AMI ID** box in the **Server** section of the **Configuration** tab for your environment in the AWS Toolkit for Eclipse\. 

**Important**  
Using your own AMI is an advanced task that you should do with care\. If you need a custom AMI, we recommend you start with the default Elastic Beanstalk AMI and then modify it\. To be considered healthy, Elastic Beanstalk expects Amazon EC2 instances to meet a set of requirements, including having a running host manager\. If these requirements are not met, your environment might not work properly\.