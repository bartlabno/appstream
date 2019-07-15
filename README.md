# appstream
Appstream - Ansible playbook which triggers CloudFormation templates to manage AppStream 2.0 on AWS

# Playbook
There are two main tasks which manages AppStream. One can be used on existing VPC configuration, when other one creates separate VPC will all InternetGateways etc. 

# AWS
You need fully accessible AWS account with all mandatory variables as env variables to trigger this playbook

# CloudFormation
As CloudFormation templates aren't as great as Terraform, but from the other hand these supports AppStream, so for workaround of loops and some variable conditionals I am using Ansible templates over CloudFormation templates to make sure everyting during the deployemnt is in place

All Cloudromation templates are hidden as jinja2 templates. Please browse into [templates](./roles/appstream/templates/appstream.yaml.j2)

# How to use it?
Simple clone this repository or use ansible-pull. Create users.yaml file or edit existing one adding email and surname as mandatory, where name is only optional. Remeber, due to some template restrictions surname can contain only alphanumeric symbols [a-z0-9]

```ansible-playbook site.yaml --extra-vars @users.yaml```

# Variables
users are being stored by default in users.yaml file, away from defaults. defaults/main.yaml contain all mandatory and optional variables which you can add using ansible specific best practicies for variables. By default please do not touch defaults.yaml!

# ImageBuilder
Unfortunately, Image Builder doesn't support some Powershell scripting and automation on creation of Images. That's why ImageBuilder to creation of base Image has been done manually by myself. In this case scenario it is OpenOffice

# OpenOffice?
This is my demo stack for some specific purposes, you can stream mostly whatever you want. Don't forget you need AWS account and software license.
