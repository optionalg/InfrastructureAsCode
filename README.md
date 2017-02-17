# InfrastructureAsCode
### Cloudformation templates standing up a AWS Scenario 2 VPC stack with Docker Hello-World Instances

Running the following command from a machine properly configured with the AWS cli interface will stand up an AWS Scenario 2 VPC which pulls the current Docker Hello-World image. The Hello World output is available as text hosted by httpd.

```json
aws cloudformation create-stack --stack-name sfsherwani-helloworld --template-url https://s3.amazonaws.com/sfsherwani-s3-170217/nested.template
```
The VPC infrastructure that is created can be viewed in the following image.

![alt text](https://github.com/PacoGuy/InfrastructureAsCode/blob/master/VPC_diagram.png "VPC Diagram")

This VPC was created to be a high availability cluster with the Elastic Load Balancer in the public subnet. All Amazon Linux instances launched by the Docker nested stack are launched into the private subnets.

The subnets are split between two availability zones for disaster preparedness, and the instances are launched in a balanced manner between the two zones.

![alt_text](https://github.com/PacoGuy/InfrastructureAsCode/blob/master/Webserver_diagram.png "Docker Stack Diagram")

In order to specify the number N instances required a change must be made to the the Docker.template file at the "NumberOfInstances" : "Default" Parameter. This parameter accepts any number type input. This file can be found at https://github.com/PacoGuy/InfrastructureAsCode/blob/master/docker.template

Given more time to complete the challenge to my satisfaction I would modify the Nested.template stack to accept a parameter for the N number of instances directly so that it can be defined in the cli command directly and passes through to the correct nested template.

The templates are configured in such a way that the same templates can be used multiple times in the same region without namespace conflicts, utilizing the stack name and resource ids to create unique names for all resources.

The Docker Hello-World image did not output to httpd directly so the command line output is piped to the index.html file and served through the load balancer.

Reference templates used to build this project are available upon request.
