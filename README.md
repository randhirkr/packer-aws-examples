# packer-aws-examples

### AMI customization using the latest Amazon linux2 AMI. 
**Note:** Change parameter values as needed.
```
packer build \
-var 'aws_region=us-east-1' \
-var 'aws_vpc_id=<vpc-id>' \
-var 'vpc_subnet_id=<subnet-id>' \
-var 'ec2_temp_sg_ip_cidr=<ip-cidr>' \
-var 'ec2_instance_type=t4g.micro' \
-var 'ami_arch=arm64' \
amz-linux2-latest-ami-httpd.json

Test the httpd server:
http://<ec2-public-ip>
```

### AMI customization using custom Amazon linux2 AMI. 
**Note**: Change parameter values as needed.
```
packer build \
-var 'aws_region=us-east-1' \
-var 'aws_source_ami=<ami-id>>' \
-var 'aws_vpc_id=<vpc-id>' \
-var 'vpc_subnet_id=<subnet-id>' \
-var 'ec2_instance_type=t2.micro' \
-var 'ec2_temp_sg_ip_cidr=<ip-cidr>' \
amz-linux2-ami-lamp.json

Test the lamp server:
http://<ec2-public-ip>/phpinfo.php
```

### Reference:

https://www.packer.io/docs/builders/amazon/ebs

https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeImages.html

https://aws.amazon.com/blogs/mt/creating-packer-images-using-system-manager-automation/

For querying the latest AMI, refer to below link for owners list:
https://aws.amazon.com/blogs/devops/how-to-create-an-ami-builder-with-aws-codebuild-and-hashicorp-packer/
