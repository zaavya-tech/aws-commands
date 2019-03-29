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