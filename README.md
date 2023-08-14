**EC2 Instance with Squid Proxy CloudFormation Template - README**

This CloudFormation template allows you to easily deploy EC2 instances configured with a Squid proxy server in an Amazon Web Services (AWS) environment. The Squid proxy server can be used to enhance security, optimize network traffic, and cache frequently accessed content.

**Prerequisites:**

1. AWS Account: Ensure you have an active AWS account.
2. AWS CLI (Command Line Interface): Install and configure the AWS CLI on your local machine.
3. Basic understanding of AWS CloudFormation and EC2 instances.

**Usage:**

1. **Clone the Repository:**
   Clone this GitHub repository to your local machine:

   ```bash
   git clone https://github.com/ericsoi/ec2-squid-proxy-cloudformation.git
   cd ec2-squid-proxy-cloudformation
   ```

2. **Deploy the Stack:**
   Deploy the CloudFormation stack using the AWS CLI. Replace `stack-name` with a name of your choice:

   ```bash
   aws cloudformation create-stack --stack-name squid-proxy-stack --template-body file://template.yaml --capabilities CAPABILITY_IAM
   ```

4. **Access the Squid Proxy:**
   Once the stack creation is complete, you will find the EC2 instance's public IP in the CloudFormation stack outputs. Use this IP along with the configured `ProxyPort` to configure your applications or network devices to use the Squid proxy.
   Alternatively, you can get the output by running the following

   ```bash
   aws cloudformation describe-stacks --stack-name squid-proxy-stack --region us-east-2 --query "Stacks[0].Outputs[].OutputValue" 
   ```

5. **Cleaning Up:**
   To avoid incurring unnecessary charges, don't forget to delete the CloudFormation stack when you're done using the proxy:

   ```bash
   aws cloudformation delete-stack --stack-name squid-proxy-stack
   ```