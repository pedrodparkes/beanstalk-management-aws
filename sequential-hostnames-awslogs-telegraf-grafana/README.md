## Description
This .ebextension can be placed inside any beanstalk-code repo and realize:
 - importing IAM user's ssh public keys to /home/ec2-user/.ssh/authorized_keys;
 - setup awslogs agent;
 - configure awslogs filestreaming;
 - configure awslogs filtering and alerting (commented);
 - set sequential hostnames on beanstalk instances and set EC2 tag <CNAME> for DynDNS;
 - Install and configure Telegraf (https://www.influxdata.com/time-series-platform/telegraf/);

 ## Usage
 Place .ebextensions dir in your beanstalk repo or project folder

## Configuration
Edit cwl-setup.config section here:
```
[[outputs.influxdb]]
	urls = ["http://YourGrafanaHostName:8086"] # required
    database = "InfluxDB.Name" # required
    retention_policy = ""
    write_consistency = "any"
    timeout = "5s"
    username = "InfluxDB.UserName"
    password = "InfluxDB.Password"
```

and here:
```
# BEGIN CONFIGURATION
	# Set these variables accordingly
    DOMAIN=Route53LocalDomain
    AWS_REGION=us-east-1
```