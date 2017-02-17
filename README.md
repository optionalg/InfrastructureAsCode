# InfrastructureAsCode
Cloudformation templates standing up a AWS Scenario 2 VPC stack with Docker Hello-World Instances

Running the following command from a machine properly configured with the AWS cli interface will stand up an AWS Scenario 2 VPC which pulls the current Docker Hello-World image. The Hello World output is available as text hosted by httpd.

```json
aws cloudformation create-stack --stack-name sfsherwani-helloworld --template-url https://s3.amazonaws.com/sfsherwani-s3-170217/nested.template
```
The VPC infrastructure that is created can be viewed in the following image.

![alt text](InfrastructureAsCode/VPC_diagram.png "VPC Diagram")
