# AWS Build a Serverless Web Application Project

Welcome to the "Build a Serverless Web Application" project on AWS! This project will guide you through the process of creating a serverless web application using various AWS services. By the end of this project, you'll have a fully functional web application that can dynamically display and manage data.

## Project Overview

In this project, you will build a serverless web application that allows users to view, add, edit, and delete data items. You will use a combination of AWS services, including AWS Lambda, Amazon API Gateway, Amazon DynamoDB, AWS S3, and AWS CloudFormation.

The application you'll build will have the following features:
- Display a list of items retrieved from a DynamoDB database.
- Allow users to add new items to the database.
- Enable users to edit and update existing items.
- Provide the ability to delete items from the database.

## Prerequisites

Before you start this project, make sure you have the following prerequisites in place:
- An AWS account. If you don't have one, you can sign up for an account on the [AWS website](https://aws.amazon.com/).
- AWS Command Line Interface (CLI) installed on your local machine. You can download and install it from the [AWS CLI documentation](https://aws.amazon.com/cli/).
- Basic knowledge of AWS services like Lambda, API Gateway, DynamoDB, S3, and CloudFormation.

## Getting Started

1. **Clone the Repository:** Start by cloning the project repository from GitHub.
   ```
   git clone <repository-url>
   ```

2. **Set Up AWS Credentials:** Configure your AWS CLI with the necessary credentials to access your AWS account.
   ```
   aws configure
   ```
   Follow the prompts to provide your AWS Access Key ID, Secret Access Key, preferred region, and output format.

3. **Create DynamoDB Table:** Use CloudFormation to create the DynamoDB table for storing data. Navigate to the project directory and deploy the CloudFormation stack.
   ```
   aws cloudformation create-stack --stack-name MyDynamoDBStack --template-body file://dynamodb-stack.yaml
   ```
   Wait for the stack to be created successfully.

4. **Deploy Lambda Functions:** Deploy the Lambda functions using the provided deployment scripts.
   ```
   ./deploy-lambdas.sh
   ```

5. **Create API Gateway:** Create an API Gateway to expose the Lambda functions as RESTful APIs.
   ```
   ./create-api-gateway.sh
   ```

6. **Configure S3 Bucket:** Create an S3 bucket to host the static web content.
   ```
   aws s3 mb s3://my-web-app-bucket
   ```

7. **Deploy Web Application:** Deploy the web application files to the S3 bucket.
   ```
   aws s3 sync ./web-app/ s3://my-web-app-bucket
   ```

8. **Access Your Application:** Once the deployment is complete, access your web application using the S3 bucket's public URL.

## Usage

- Launch your web application using the provided S3 URL.
- Explore the application's interface to view, add, edit, and delete data items.

## Clean Up

After you've finished experimenting with the project, make sure to clean up the resources to avoid incurring unnecessary charges.

1. Delete the CloudFormation stack.
   ```
   aws cloudformation delete-stack --stack-name MyDynamoDBStack
   ```

2. Delete the S3 bucket and its contents.
   ```
   aws s3 rb s3://my-web-app-bucket --force
   ```

3. Delete the API Gateway.
   ```
   ./delete-api-gateway.sh
   ```

## Conclusion

Congratulations! You've successfully built a serverless web application using AWS services. This project demonstrates how to leverage various AWS components to create a fully functional application without managing traditional server infrastructure. You can further enhance and customize the application based on your requirements.

For more information and advanced features, refer to the official AWS documentation and explore additional AWS services. Happy coding!
