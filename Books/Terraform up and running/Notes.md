https://www.amazon.com/Terraform-Running-Writing-Infrastructure-Code/dp/1098116747/ref=sr_1_2

Progress: 23/415

# Why Terraform?

- The goal of DevOps is to automate as much of the software delivery process as possible.
- The idea behind infrastructure as code (IaC) is that you write and execute code to define, deploy, update and destroy your infrastructure.
- IaC tool categories:
	- configuration managment tools (install and manage software)
		- chef
		- puppet
		- ansible
	- server templating tools
		- docker
		- packer
		- vagrant
	- orchestration tools
		- Kubernetes
		- Marathon/Mesos
		- Amazon ECS
		- Docker Swarm
		- Nomad
	- provisioning tools
		- Terraform
		- Cloud Formation
		- OpenStack Head
		- Pulumi

IaC benefits:
- self-service
	- people other than system admins can deploy
- speed and safety
	- Deploy process automation increases velocity and predictability
- documentation + version control
	- Infrastructure is defined in code. This provides a sort of documentation and can be tracked using version management
- Validation
	- automated testing
- reuse
	- package infrastructure into reusable and composable modules
- happiness
	- manually managing infrastructure sucks - automation is good

Terraform Overview:

HashiCorp releases a binary called terraform written in Go which allows you to manage your infrastructure on one or many different platforms (AWS, Azure, GCP, DigitalOcean, OpenStac, etc). Terraform knows how to make these API calls correctly by the configuration files you give it. Terraform does not support transparent portability between services from different cloud providers. Instead it allows you to write code that is specific to each provider with a common language, toolset, and set of IaC practices.


