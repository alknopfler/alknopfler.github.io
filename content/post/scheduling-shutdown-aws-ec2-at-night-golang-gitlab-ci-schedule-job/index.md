---
title: "Scheduling shutdown aws EC2 at night - Golang & gitlab-ci schedule job"
date: "2021-01-20"
---

When you're working with AWS sometimes you need to keep in your mind to shutdown at night the instances in order to avoid unexpected costs at the end of the month. Obviously you could do it manually but, I will offer a very simple way to do that automatically directly running a code using just a gitlab-ci pipeline.

The main components are:

- Golang code to connect to your aws account and stop the instances which are running
- Gitlab-ci pipeline but using and scheduled job to automate at night the script execution

## Golang code:

```golang
package main

import (
   "fmt"
   "github.com/aws/aws-sdk-go/aws"
   "github.com/aws/aws-sdk-go/aws/session"
   "github.com/aws/aws-sdk-go/service/ec2"
   "log"
)

func main() {
   ec2svc := ec2.New(session.New())
   params := &ec2.DescribeInstancesInput{
      Filters: []*ec2.Filter{
         {
            Name:   aws.String("instance-state-name"),
            Values: []*string{aws.String("running"), aws.String("pending")},
         },
      },
   }
   resp, err := ec2svc.DescribeInstances(params)
   if err != nil {
      fmt.Println("there was an error listing instances in", err.Error())
      log.Fatal(err.Error())
   }
   fmt.Println("Deleting instances... ")
   for idx, res := range resp.Reservations {
      fmt.Println("  > Reservation Id", *res.ReservationId, " Num Instances: ", len(res.Instances))
      for _, inst := range resp.Reservations[idx].Instances {
         fmt.Println("    - Stopping Instance ID: ", *inst.InstanceId)
         input := &ec2.StopInstancesInput{
            InstanceIds: []*string{
               aws.String(*inst.InstanceId),
            },
         }
         _, err := ec2svc.StopInstances(input)
         if err != nil {
            fmt.Println("there was an error stopping instances", err.Error())
            log.Fatal(err.Error())
         }

      }
   }
}
```

Mainly you connect using your environment access and secret key to aws ec2 in order to get all the instances which are running or maybe pending, and with the second part of the script, you stop the instances which match with the first criteria.


## Gitlab-ci Pipeline:

Just to create the pipeline, you could use the golang pipeline auto-devops tool (directly using the gitlab tool once you uploaded you first commit with the auto-devops tool).

This tools will create in your repo the next file:
```yaml
# This file is a template, and might need editing before it works on your project._
image: golang:latest

variables:
  # Please edit to your GitLab project_
  REPO_NAME: gitlab.com/alknopfler/shutdown-alk-ec2
  BINARY_NAME: shutdownec2

# The problem is that to be able to use go get, one needs to put
# the repository in the $GOPATH. So for example if your gitlab domain
# is gitlab.com, and that your repository is namespace/project, and
# the default GOPATH being /go, then you'd need to have your
# repository in /go/src/gitlab.com/namespace/project
# Thus, making a symbolic link corrects this._
before_script:
  - mkdir -p $GOPATH/src/$(dirname $REPO_NAME)
  - ln -svf $CI_PROJECT_DIR $GOPATH/src/$REPO_NAME
  - cd $GOPATH/src/$REPO_NAME

stages:
  - test
  - build
  - deploy
  - run

format:
  stage: test
  script:
    - go fmt $(go list ./... | grep -v /vendor/)
    - go vet $(go list ./... | grep -v /vendor/)
    - go test -race $(go list ./... | grep -v /vendor/)

compile:
  stage: build
  script:
    - go build -race -ldflags "-extldflags '-static'" -o $CI_PROJECT_DIR/$BINARY_NAME
  artifacts:
    paths:
      - $BINARY_NAME

run:
  stage: run
  script:
    - ./$BINARY_NAME
    
``` 


and that's all!!! the next commit will trigger the pipeline job directly, buttttt, this is just to stop the instances when the pipeline is triggered.

The last step we need to do is create a schedule job to launch automatically at night:

[![](https://alknopfler.files.wordpress.com/2021/01/image.png?w=1024)](https://alknopfler.files.wordpress.com/2021/01/image.png)

Now, you have to modify the pipeline variables in order to add your access key and secret key as well as your aws region:

[![](https://alknopfler.files.wordpress.com/2021/01/image-1.png?w=1024)](https://alknopfler.files.wordpress.com/2021/01/image-1.png)

Now, you don't have to be worry about this kind of things any more ;)
