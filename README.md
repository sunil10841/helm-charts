
**Guide to deploy Jenkins and WebApp application chart on EKS.**

Here we We 2 charts named Jenkins and WebApp.

**Jenkins**: It is Continuous integration and Continuous Deployment tool which is helping us to build docker images and pushing to ECR.
**Webapp**: A Sample Hello world app which we are deploying into tomcat docker image.

For Helm Charts folder strucure is like below:


![image](https://user-images.githubusercontent.com/90410791/132857536-210f53fe-e5aa-446b-9892-3c21666b8946.png)

Inside Templates folder we have Kubernetes manifest/objects yaml file like Deployment,service.

![image](https://user-images.githubusercontent.com/90410791/132857588-d532c8b6-6fb6-4a36-9e2c-ac89372819d6.png)

Manifest under templates directory takes values from **Values.yaml** file. Sample Values.yaml for WebApp application

```
replicaCount: 1
containePort: 8080
image:
  repository: 484183570034.dkr.ecr.us-east-1.amazonaws.com/webapp
  pullPolicy: IfNotPresent  
  tag: "17"


service:
  type: LoadBalancer
  port: 80
```
To modify any chart we just need to do the changes in values.yaml file and install the chart.

To install or upgrade any chart we need to run below commands:

```
helm upgrade --install RELEASE_NAME CHART_PATH/

```

Once we do it we get the output like below:

![image](https://user-images.githubusercontent.com/90410791/132858490-db1d26de-67d1-418c-be51-d59f929a9393.png)


































