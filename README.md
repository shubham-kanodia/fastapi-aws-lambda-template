# FastAPI Serverless Deployment Template
 
### Setup

* Install SAM using homebrew

```shell
brew tap aws/tap
brew install aws-sam-cli
```

* Check your installation

```shell
sam --version
```

* Build your project

```shell
sam build
```

* Setup credentials

    * Create a directory ~/.aws
    * Create an IAM user account and get your access key and secret key
    * Paste the following in ~/.aws/credentials
      ```shell
        [default]
        aws_access_key_id = YOUR_ACCESS_KEY
        aws_secret_access_key = YOUR_SECRET_KEY
        region = YOUR_REGION
        ```
    * Your IAM credentials need access to S3, IAM, CloudFormation and Lambda permissions

* Push the object to AWS s3 bucket

```shell
sam package --output-template-file packaged.yaml --s3-bucket invictus-deployment-artifacts --region us-east-1
```

* Deploy the application

```shell
sam deploy --template-file packaged.yaml --stack-name <your-stack-name> --region <your-region> --capabilities CAPABILITY_IAM
```