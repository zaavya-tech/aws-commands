# Introduction

Purpose of this repository is to manage all the command line scripts for AWS, serverless and bastion environments

# Commands

### S3

1. Command to copy all the files from local folder to S3 folder with kms keys algorithms
```sh
$ aws s3 cp --recursive ./ s3://my-top-secret-s3-bucket/my-top-secret-s3-bucket-folder/ --sse aws:kms --sse-kms-key-id arn:aws:kms:<enter-kms-key-here> --profile my-profile
```

2. Command to print the count of files in a directory with a specific patten
```sh
$ aws s3 ls s3://my-top-secret-s3-bucket/my-top-secret-s3-bucket-folder/ --recursive --profile my-profile | grep 'Specific_Pattern' | wc -l
```

3. Command to list the files in a in a human readable pattern
```sh
$ aws s3 ls --summarize --human-readable --recursive s3://my-top-secret-s3-bucket/my-top-secret-s3-bucket-folder --profile my-profile
```

### Bastion

1. Connect using SSH tunnels with AWS EC2 instances for different services
```sh
$ ssh -i <pemfile>.pem ec2-user@<ip> -L <port1>:vpc-nmg-pim-prod-elasticsearch-4bvzvuusickyvdokjq5s65227q.us-west-2.es.amazonaws.com:<port2>
```
* pemfile: refers to your pem file 
* ip: IP of the EC2 instance you are attempting to connect to.
* port1: refers to the inbound port, the port you will be listening on.
* port2: refers to the outbound port, the port you want to listen to. this can depends on the services (Neptune has 8182, Elasticsearch has 443, Elasticache 6379 etc)


### SSM

1. Get SSM parameters by path with profile
```sh
$ aws ssm get-parameters-by-path --path "/my/specific/path/" --profile my-profile
```

### Cloudwatch

1. AWS command to describe-log-streams for a log-group
```sh
$ aws logs describe-log-streams --log-group-name "my-log-group" --profile my-profile
```
2. AWS command to get log-events from a log-streams and a log-group
```sh
$ aws logs get-log-events --log-group-name "my-log-group" --log-stream-name "2019/03/08/[$LATEST]d105ddde6fb74a13984cb422eb841c96" --profile my-profile
```