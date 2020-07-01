---
title: "Creating Ec2 Instances Swarm"
date: 2020-06-02T15:25:08+01:00
draft: false
---




```
sudo yum -y update
```

```
sudo yum -y install docker
```

```
sudo usermod -a -G docker ec2-user
```

```
sudo chkconfig iptables off
```

```
sudo service docker start
```