# Infrastructure as Code (IaC)
Infrastructure as Code (IaC) is the managing and provisioning of infrastructure through code instead of through manual processes.
The servers can be configured by using one of the two ways:

- Push configuration: The controlling server pushes the configuration to the destination system.

- Pull configuration: the to be configured server pulls its configuration from the controlling server.

## Benefits

- Cost reduction 
  - You don’t have to hire a team of professionals to routinely manage resource provisioning, configuration, troubleshooting, hardware setup, and so on. It saves time and money
- Increase in speed of deployments
  - IaC automates resource provisioning across environments, from development to deployment, by simply running a script. It drastically accelerates the software development life-cycle and makes your organization more responsive to external challenges.
- Reduce errors
  - No human errors when as you are running a file rather than manually creating servers
- Improve infrastructure consistency
  - running the script will create identical infrastructure

## Configuartion Mangement & Orchestration
- Configuration management tools like Chef, Puppet, and Ansible help configure the software and systems on this infrastructure that has already been provisioned.
- Orchestration tools, which include Terraform and AWS CloudFormation, are designed to automate the deployment of servers and other infrastructure.
