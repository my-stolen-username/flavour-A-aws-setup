# flavour-A-aws-setup


## Setting up AWS Resource Group

1. Open the Resource Group console at https://console.aws.amazon.com/resource-groups
2. In **Create Resource Group**, select Tag Based.
3. Add two tags with: 
    ![step3](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/aws-resource-group/step3.png)
    1. Key rg-gw-dev and name rancher
    2. Key rg-gw-dev and name k8s-node
4. These will be used later when creating EC2 instances for rancher and k8s
    ![step4](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/aws-resource-group/step4.png)
5. Add group name then choose **Create Group**


## Setting up AWS EC2 instance for Rancher for Flavour A

1. Open the EC2 console at https://console.aws.amazon.com/ec2/
2. Click on instances
 ![step2](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step2.png)
3. Launch instances
 ![step3](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step3.png)
4. In **Step 1: Choose an Amazon Machine Image (AMI)**, Select **Ubuntu Server 20.04 LTS (HVM), SSD Volume Type**.
 ![step31](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step31.png)
5. In **Step 2: Choose an Instance Type**, For Flavour A, We went with t3a.medium(Mostly because we don’t know at this point in time how much resource the applications are going to consume)  choose **Next: Configure Instance Details**.
 ![step32](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step32.png)
6. In **Step 3: Choose an Instance Type**, Leave everything to default and choose **Next: Add Storage**.
 ![step331](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step331.png)
 ![step332](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step332.png)
7. In **Step 4: Add Storage**, change size to 30GB then choose **Next: Add Tags**
 ![step34](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step34.png)
8. In **Step 5: Add Tags**, add a tag with key rg-gw-dev and name rancher i.e the tag we added in our Resource Group. The tag should match the one you created in Resource Group since we are using Resource Group based on tags. Choose **Next: Configure Security Group**
 ![step35](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step35.png)
9. In **Step 6: Configure Security Group**, select Create a new security group if not previously created. Give the name and description for the security group. Leave everything to default and choose **Next: Review Instance Launch**
 ![step36](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step36.png)
10. In **Step 7: Review Instance Launch**, review everything and **Click on Launch**
11. Download the key pair to ssh into the server later. If you don’t download the keypair now you won’t be able to in the future
 ![step37](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/ec2-for-rancher/step37.png)
12. Launch instances
  

## Associate Elastic IP to Rancher Instance
The public ip AWS assings isn't persistent and will change everytime you shutdown the instace.So, you'll need to set-up an Elastic IP.
1. Open the EC2 console at http://console.aws.amazon.com/ec2
2. Select **Elastic IP** and click on **Allocate Elastic IP address**
   ![step2](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/elastic-ip/step2.png)
3. Choose **Allocate**
   ![step3](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/elastic-ip/step3.png)
4. Select the newly created Elastic IP, choose actions then choose **Associate IP address**
   ![step4](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/elastic-ip/step4.png)
5. Select the Rancher instance and select the private ip that has been associated with the rancher instance.Choose **Associate**
   ![step5](https://github.com/my-stolen-username/flavour-A-aws-setup/tree/main/img/elastic-ip/step5.png)


