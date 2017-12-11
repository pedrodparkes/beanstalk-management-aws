## Description

This script figures out a hostname based on the value of BeansTalk environment name.
E.g, "someapp" would result in the hostname someapp-xxx
where "xxx" is the next available number. The hostname is set locally and
a CNAME record in Route53 can be created by separate Lambda Job.
https://github.com/awslabs/aws-lambda-ddns-function
Or my DDNS fork from this repo ../dns-management/aws-route53-dyndns

The FQDN becomes HOSTNAME . ENVIRONMENT . DOMAIN
(e.g. someapp-dev-000.mydomain)

Finally the hostname is set on the "Name" tag of the ec2 instance

## Dependencies:
This script assumes that the following
packages are installed:
```
* route53-cli
* aws cli
* ec2-metadata
```

## Tested on Amazon Linux BeansTalk AMI (Java and Node.js)

Running the script from .ebextension.yaml
```
	setsid /tmp/cwlogs/sethostname.sh `{"Ref":"AWSEBEnvironmentName"}` && exit 0;
	/usr/sbin/onboot.sh
```

## Requirements:
  EC2 instance must have access to IAM-users and keys.
  Create IAM role by CloudFormation template iam-role-importer.yaml

## Tested on Amazon Linux AMI and Ubuntu

## Installation:
```
	/tmp/cwlogs/sethostname.sh
	chmod 700 /tmp/cwlogs/sethostname.sh
```

## Configuration:
	Change accordingly: 
```
		DOMAIN=mydomain
		AWS_REGION=us-east-1
```