# AWS Lambda API (Terraform Project)

This project deploys a simple serverless API using AWS Lambda and API Gateway, managed entirely with Terraform.  
The API returns a plain text response and is designed as a minimal example of how to build and deploy a Lambda-backed HTTP endpoint.

---

## Overview

The infrastructure includes:

- API Gateway (HTTP API)
- Lambda function
- IAM role and policy for Lambda execution
- Terraform configuration to manage all resources

When you call the endpoint, the Lambda function returns:

```
Hello from Lambda API!
```

---

## Architecture

1. API Gateway receives the HTTP request  
2. API Gateway triggers the Lambda function  
3. Lambda executes the Python handler  
4. The response is returned to the client  

---

## Project Structure

```
aws-lambda-api-terraform/
├── lambda/
│   └── lambda_function.py
├── lambda.zip
├── main.tf
├── providers.tf
├── outputs.tf
├── variables.tf
└── .gitignore
```

---

## Deployment

### Initialize Terraform

```
terraform init
```

### Apply the configuration

```
terraform apply
```

Terraform will output the API endpoint, for example:

```
api_endpoint = "https://xxxxx.execute-api.ap-northeast-1.amazonaws.com"
```

Open the URL in your browser to test the API.

---

## Testing

Using curl:

```
curl https://<your-endpoint>
```

Expected output:

```
Hello from Lambda API!
```

---

## Lambda Function

The Lambda handler is a simple Python function:

```python
def handler(event, context):
    return {
        "statusCode": 200,
        "body": "Hello from Lambda API!"
    }
```

The file is packaged into `lambda.zip` and deployed by Terraform.

---

## .gitignore

The repository excludes:

- .terraform/
- Terraform state files
- Provider binaries
- Python cache files

This keeps the repository clean and avoids committing large files.

---

## Notes

This project is a basic example of using Terraform to deploy a Lambda function behind an HTTP API.  
It can be extended with additional routes, environment variables, or integrations such as DynamoDB.
