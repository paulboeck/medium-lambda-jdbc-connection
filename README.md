# medium-lambda-jdbc-connection

This project is meant to be an example of how to create and deploy an AWS Lambda function 
written in Java. The Lambda function uses the AWS SDK for Java to retrieve a secret from
AWS Secrets Manager and then uses the secret to connect to a database. The Lambda function
then executes a query against the database and returns the results.
There is no trigger defined for the lambda so it can only be invoked by using the Test feature in
the AWS Lambda console or via the SAM CLI.

## Assumptions 
- you have installed the AWS CLI and configured it with your AWS credentials 
- you have installed terraform
- you have installed SAM CLI
- you have created an S3 bucket to store the Lambda function package
- Commands in this document are specified for a Linux or Mac OS X environment. If you are using
  Windows, you will need to adjust the commands accordingly.

## Setup
These command should be run from the `./terraform` folder of the project/repository
- Run `export AWS_PROFILE=<your-aws-profile>` to set the AWS profile to use
- Run `terraform init` to initialize the terraform project
- Run `terraform apply` to create the RDS instance and the secret in AWS Secrets Manager
    - You will be prompted to enter a value for the `db-password` and `db-username` variables. These are the 
      the database password and username respectively

## AWS SAM
These command should be run from the root folder of the project/repository
- Run `sam build --template-file sam.template.yaml` to build the Lambda function package
- Run `sam deploy 
  --template-file .aws-sam/build/template.yaml 
  --no-confirm-changeset  
  --no-fail-on-empty-changeset  
  --stack-name simple-java-lambda 
  --s3-bucket <your-s3-bucket> 
  --capabilities CAPABILITY_IAM  CAPABILITY_NAMED_IAM 
  --region <your region>` to deploy the Lambda function to AWS Lambda