# Elastic Container Service
------------------------------------------------------------------------------------
* create a cluster in ecs. here we have have 2 options,
  * fargate.
  * ec2 instance.
* in k8s has smallest unit is `pod`.
  * pod is defining how u r container would look like?
    * resources for container
    * volumes required for container
    * it is a defintion how a container needs to run.
* in ecs we have `task defintion`.in the task defintion u would explain,
  * how does u r container look like?
  * we have `taskdefintion.yaml`.
  * when u implement this task defintion that will create a `task`.
  * task is the one that is actually running u r container.
  * once containers are runnering we can create `services`. and this services will add the loadbalencing capabilities.
  * using this services u can create the `ingress policies`, u can attach with that application loadbalencer.

## demo
--------------------------------------------------------------------------------------
![preview](./images/ecs1.png)
![preview](./images/ecs2.png)
![preview](./images/ecs3.png)
* we can do cluster creation commandline as well.
![preview](./images/ecs4.png)
![preview](./images/ecs5.png)
![preview](./images/ecs6.png)
![preview](./images/ecs7.png)
![preview](./images/ecs8.png)
* it will take very very less time when we r using fargate instances.
* when we use fargate instances everything will create automatically.they r the runtime configurations.
![preview](./images/ecs9.png)
![preview](./images/ecs10.png)
* ecs has a default cloudwatch monitering alerting enabled.

### first build the docker image
----------------------------------------------------------------------------------------
* we have to build the docker image first, push that docker image to `ecr container registry`.

## ECR
------------------------------------------------------------------------------------
* create a private repo in ecr.
![preview](./images/ecs11.png)
![preview](./images/ecs12.png)
* we need to build a docker image by executing the command.
```
docker build -t <registry_name/repo_name:tag> .
```
![preview](./images/ecs13.png)
* before build the image we need to login into ecr.
![preview](./images/ecs14.png)
![preview](./images/ecs15.png)
![preview](./images/ecs16.png)
* push the docker image.
![preview](./images/ecs17.png)
* now we create a task defintion.
![preview](./images/ecs18.png)
![preview](./images/ecs19.png)
* we can create the task defintion cli as well.
![preview](./images/ecs20.png)
![preview](./images/ecs21.png)
![preview](./images/ecs22.png)
![preview](./images/ecs23.png)

### task role and task execution role
--------------------------------------------------------------------------------------
* when container is running this container might need access to the other things.
  * lets say container wants to talk to s3 bucket.
  * container wants to talk to cloudwatch service.
  * container wants to talk with any other service of aws platform.
  * for this we need a `task role`.
![preview](./images/ecs24.png)
* if it is ok if u dont have a `task role`,but u need to create a new `task execution role`.
![preview](./images/ecs25.png)
* now give the container details.
![preview](./images/ecs26.png)
* u can add multiple ports what port u r application is running on.
![preview](./images/ecs27.png)
![preview](./images/ecs28.png)
![preview](./images/ecs29.png)
![preview](./images/ecs30.png)
* the task defintion u created is now in active status.
![preview](./images/ecs31.png)
* container is not active but the task definiton is active.
![preview](./images/ecs32.png)
* in the acations in task definition `deregister` the task definition will be deleted.
![preview](./images/ecs33.png)
* once u r task defintion is in active status, u need to goto `deploy` and execute the `run task`.
![preview](./images/ecs34.png)
![preview](./images/ecs35.png)
![preview](./images/ecs36.png)
![preview](./images/ecs37.png)
![preview](./images/ecs38.png)
* if u want to add any details here u can modify the `task overrrides`.
![preview](./images/ecs39.png)
* u can provide any container overrides as well.
![preview](./images/ecs40.png)
![preview](./images/ecs41.png)
* now task will be launched and task is provisioning.
![preview](./images/ecs42.png)
* `task definition.yaml` is very similar to `pod.yaml`, where u provide entire specification.but the implementation of u r task definition is u r `task`.
* this `task` will run u r `container`.
![preview](./images/ecs43.png)
* using a `task defintion`  have created a `task` that task is running a `container` on u r `cluster`.
![preview](./images/ecs44.png)
![preview](./images/ecs45.png)
![preview](./images/ecs46.png)
![preview](./images/ecs47.png)
![preview](./images/ecs48.png)



