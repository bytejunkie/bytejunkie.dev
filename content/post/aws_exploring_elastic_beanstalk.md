---
title: "AWS: exploring Elastic Beanstalk"
date: 2020-05-18T09:01:32+01:00
draft: true
---

After 4 years building Service Fabric platforms, Containers have been noise that I've heard, but not really understood. Which means they were the first thing to dabble in when I found some free time in lockdown. 

I started out with the excellent [Docker Deep Dive](https://www.amazon.co.uk/Docker-Deep-Dive-Nigel-Poulton/dp/1521822808/ref=sr_1_1?dchild=1&keywords=docker+deep+dive&qid=1589790965&sr=8-1) book by [Nigel Poulton](https://www.amazon.co.uk/Docker-Deep-Dive-Nigel-Poulton/dp/1521822808/ref=sr_1_1?dchild=1&keywords=docker+deep+dive&qid=1589790965&sr=8-1) though I found it on offer at [LeanPub](https://leanpub.com/dockerdeepdive).

I'm probably still only half of the way through this book, but decided it was time to try out some of the knowledge. 

I've repurposed the Flask App in this [tutorial](https://docker-curriculum.com/) which shows originally, random cat gifs. My version which can be found [here](https://hub.docker.com/repository/docker/bytejunkie77/carpics), shows pictures of Modified German cars, which is a bit of a passion of mine. 

I've also uploaded the container app to Elastic Container Registry in another blog post here.

To the point of this post, [here](https://github.com/bytejunkie/tf-aws-eba) is a boilerplate repo which creates an Elastic Beanstalk app. it also creates all the pre-requisites.
- IAM Role to allow the EC2 instance to write log files
- IAM policy to attach to the above
- IAM Instance Profile to pull the above two items together
- The Elastic Beanstalk application, and version. 
- The Elastic Beanstalk Environment and Configuration Template, to create the instance on a certain ami.

These templates should be reasonably reusable, there is a readme with details of the secrets to create. 

### Things to note

There is a data object in *main.tf* which refers to a zip file of the application. From the Terraform Provider [docs](https://www.terraform.io/docs/providers/aws/r/elastic_beanstalk_application_version.html) it doesnt look like it is possible to deploy from a git repo yet, which is a shame. Essentially, you're asking EB to read a json file to work out what to deploy. But it needs to be in a zip file.

```
data "aws_s3_bucket_object" "carpics" {
  bucket = "carpics-deploy"
  key    = "source/carpics.zip"
}
```