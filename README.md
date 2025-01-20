# guacamole
Automation to  deploy a guacamole server to AWS

This repo might be superceded by an AWS EC2 template.

Assumed: AWS Linux 2023 AMI

sudo -i  or as user-data at launch

```
yum -y update
yum -y install docker python3-pip 
pip3 install --user docker-compose
usermod -a -G docker ec2-user
id ec2-user
newgrp docker
systemctl enable docker.service
systemctl start docker.service
```

mkdir ${HOME}/docker-stack
cd ${HOME}/docker-stack

mkdir -p ${HOME}/docker-stack/guacamole/init
chmod -R +x ${HOME}/docker-stack/guacamole/init
docker run --rm guacamole/guacamole:1.5.3 /opt/guacamole/bin/initdb.sh --postgresql > ${HOME}/docker-stack/guacamole/init/initdb.sql

