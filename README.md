# TERRAFORM WITH PACKER AND ANSIBLE ON AWS

[Terraform](https://www.terraform.io) is a IaC tool form hashicorp.
[Packer](https://www.packer.io/) is a automated machine image building tool from hashicorp,
while [Ansible](https://www.ansible.com/) is a IT automation from redhat.

### What is done :

A custom AMI is created with packer with docker and a container with a app prebuilt in it with ansible on AWS. [usage of ansible in the builtstage is made possible with  ansible-local provisioner of packer]

This custom AMI can be used to create infrastructure and this image will be very useful in horizontal scaling of the infrastructure when created with terraform. Since, it makes us go one step close to immutability of state and maintaince of EC2 OS by IaC code of packer. 

The `AMI` value is known after the `packer build` command , which can be set in terraform variable or hardcode them in `aws_instance` resource of terraform file. 

With terraform an `VPC` with 3 public subnet and 3 private subnet with a nat gateway  and a EC2 instance with custom ssh key uploaded by us with a predefined security  group which will allow tcp ingress on port 22 and all egress  respectively are created.