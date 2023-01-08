## Description
The templates have been separated into a network infrastructure template and a server infrastructure template. It was easier to do it this way and makes more sense rather than putting everything in a large single file and trying to determine the order of resource creation with `DependsOn`

`network-infra.yml` creates the logical network for the project. This stack should be run first.

`server-infra.yml` creates the server resources -- i.e the load balancer, security groups etc. This should only be run after the `network-infra` stack has been successfully created.

The shell scripts are a simple wrapper for the `aws cloudformation` command. They can be used by simply running the scripts and providing two parameters: Name of the stack to create and the file that contains the template

> For example: `./create.sh ThirdSemesterLogicalNetworkStack network-infra.yml`

## Instructions
1. Create the network infrastructure by running the `network-infra` stack.
2. Wait until this stack creation is completed on AWS
3. Create the server infrastructure by running the `server-infra` stack to complete the project.
4. To make things slightly easier, one of the outputs of the server-infra stack is the DNS name of the load balancer. Simply copy that out and open in a new tab. Alternatively, go to the load balancer on the console and copy out the domain name from there

> N.B. There was no need to use ansible since every requirement of the project could be completed using Cloudformation only