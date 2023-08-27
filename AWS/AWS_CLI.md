# Amazon Web Service Command Line Interface 

To get access to the AWS CLI we can use:

1. AWS Console that is located at the top-right corner of the AWS page

2. We can use docker: spin up the container with AWS CLI on it
```console
docker pull amazon/aws-cli
```

```console
docker run --rm -it amazon/aws-cli --version
```

3. Use locally

a) install CLI
b) run
```console
aws configure
```
c) provide user access data (we can list out format as json or use "table" or "yml")

## Commands

1. get aws version
```console
aws --version
```

2. get aws configuration list (will give us profile, access_key, secret_key and region)
```console
aws configure list 
```

3. get regions from our account
```console
aws ec2 describe-regions --output table --color on
```

4. This will turn on the intelisence for cli for all the different tools (for one command)
```console
aws -cli-auto-promt on
```

For all prompts, set to on
```console
$Env:aws_cli_auto_prompr="on"
```
Back to off 
```console
$Env:aws_cli_auto_prompr="off"
```

## Interact with services

### Service: s3

1. List them
```console
aws s3 ls
```

2. create one s3 (make bucket)
```console
aws s3 mb s3://marekjaskulabucket
```

3. Create new file (pass the context as file)
```
"hello aws" | Out-File - FilePath "hello.txt"
Get-Content hello.txt
```

4. upload file to s3 (source - destination)
```console
aws s3 cp hello.txt s3://marekjaskulabucket
```

5. download file from s3 
```console
aws s3 cp s3://marekjaskulabucket/hello.txt hello2.txt
```

6. Remove backet
```console
aws s3 rb s3://marekjaskulabucket --force
```

### Service: Dynamo db

Dynamo db is a key value pair data source

1. List tables
```console
aws dynamob list-tables
```

2. describe tables
```console
aws dynamodb dscribe-table --table-name movies
```