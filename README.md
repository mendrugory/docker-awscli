# Docker awscli


An AWS CLI tool in Docker container to be used in your CI/CD pipelines.

This repo triggers auto-build and push images to [Docker Hub](https://dockerhub.com/r/mendrugory/awscli).

> You must have an AWS account with access to the SDK.

## Check the version

```
$ docker run --rm  mendrugory/awscli aws --version
```

## List EC2 instances

```
$ docker run --rm \
  -e AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID} \
  -e AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY} \
  mendrugory/awscli \
  aws ec2 describe-instances --region <region>
```


## List ELB instances

```
$ docker run --rm \
  -e AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID} \
  -e AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY} \
  mendrugory/awscli \
  aws elb describe-load-balancers --region <region>
```


## List ALB instances

```
$ docker run --rm \
  -e AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID} \
  -e AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY} \
  mendrugory/awscli \
  aws elbv2 describe-load-balancers --region <region>
```


## Point to an EKS cluster

```
$ docker run -v ${HOME}:/root \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -e AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID} \
  -e AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY} \
  mendrugory/awscli \
  aws eks --region <region> \
  update-kubeconfig --name <cluster name>
```