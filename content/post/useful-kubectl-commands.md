---
title: "Useful Kubectl Commands"
date: 2020-06-23T10:07:49+01:00
draft: false
---

## Pod Basics

```
# create pod from yaml folder in current dir
kubectl apply -f pod.yml

# list running pods
kubectl get pods

# longer form info on pod
kubectl describe pods hello-pod

# run command against a pod
kubectl exec hello-pod ps aux

# run terminal in a pod - ctrl+d to exit
kubectl exec -it hello-pod sh

# delete a pod
kubectl delete -f pod.yml
```

## Deployment commands

```
# create a deployment
kubectl apply -f deploy.yml

# list the deployments
kubectl get deploy hello-deploy

# list with more info
kubectl describe deploy hello-deploy

# apply a config with the record of the command
kubectl apply -f deploy.yml --record

# see the rollout history
kubectl rollout history deployment hello-deploy

# backout a deployment
kubectl rollout undo deployment hello-deploy --to-revision=1

# view replica sets
kubectl get rs
```
