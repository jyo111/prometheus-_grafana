## Instructions

### Installation
- Install Chocolatey - For Windows instructions are here - https://chocolatey.org/install
- Install Terraform - https://learn.hashicorp.com/tutorials/terraform/install-cli

### Generate SSH key
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- SSH key is by default installed under C:\Users\<user>\.ssh
- id_rsa is the private key. You never share this key with anyone.
- id_rsa.pub is the public key

### Setup
Create a file named terraform.tfvars in line with all the other files
```
aws_access_key = "<your aws access key id>"

aws_secret_key = "<your aws secret access key id>"
```

### Terraform commands
Open command prompt at the folder where you have created files - main.tf and providers.tf
```
terraform init					[initializes your provider]

terraform plan					[shows you what resources would be created/updated/destroyed]

terraform apply	-auto-approve	[creates resources]

terraform destroy -auto-approve	[destroys resources]
```

### Get public IP
#### Get public IP from AWS Management Console
- Login to AWS web console
- Go to EC2 service
- Open the new EC2 instance that you created using Terraform
- Get the public IP

#### Get public IP from Terraform output
- Public IP of the instance would be printed on the screen when you run 'terraform apply' command
- You can also get it using 'terraform output' command


### Connect to the new EC2 instance
- Run following command in Git Bash
```
ssh -i ~/.ssh/id_rsa ec2-user@<publi_ip_address_of_ec2_instance>
```

### Miscellaneous Terraform Commands
#### Import AWS Certificate to make it managed by Terraform
```
terraform import aws_acm_certificate.jenkins-cert arn:aws:acm:us-east-1:000004345237:certificate/d89de5cd-000-45a1-8530-3d0bb0009d34
```

#### Show state of only a targeted resource
```
terraform state show aws_acm_certificate.jenkins-cert
```

terraform import aws_route53_zone.lotusops Z10145293DI6H0A5UMAJI
