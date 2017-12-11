# BeansTalk environment management

Set of scripts to manage BeanTalk environment
    *each subfolder has own README.md

### ./sequential-hostnames-awslogs-telegraf-grafana/

Provided .ebextension can be placed inside any beanstalk-code repo and realize:
 - importing IAM user's ssh public keys to /home/ec2-user/.ssh/authorized_keys;
 - setup awslogs agent;
 - configure awslogs filestreaming;
 - configure awslogs filtering and alerting (commented);
 - set sequential hostnames on beanstalk instances and set EC2 tag <CNAME> for DynDNS;
 - Install and configure Telegraf log-streaming (https://www.influxdata.com/time-series-platform/telegraf/);



### ./sequential-hostnames-bootstrap-way/
AWS Userdata script that collects existing VMs and set correct sequential hostname
Main purpose - Don't create new monitoring NODE (Grafana, icinga) for each new Instance in Autoscaling Group# beanstalk-management-aws
