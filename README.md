# medium-lambda-jdbc-connection

This project is meant to be an example of how to create and deploy an AWS Lambda function 
written in Java. The Lambda function uses the AWS SDK for Java to retrieve a secret from
AWS Secrets Manager and then uses the secret to connect to a database. The Lambda function
then executes a query against the database and returns the results.
There is no trigger defined for the lambda so it can only be invoked by using the Test feature in
the AWS Lambda console or via the SAM CLI.
