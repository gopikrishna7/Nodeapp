What I have added in this repo?
- Modified **app.js** and **.env.example** files, instead of passing MongoDB URI , 
  I have passed the username,password,host,port and DB separately so that we can separate these as kubernetes ConfigMap and Secrets.
- Added **Jenkinsfile** for End to end CI
- Added **sonar-project.properties** file for static code analysis.
- Added Kubernetes folder contains k8s manifest files.
- helm folder added.
- added argo-application.yaml file
---------------------------------------------------------------------------------------------


**Task1:**
I have used Jenkins for ci/cd , written and pushed The Jenkinsfile to the folder.


**Task2:**
I have configured webhooks-in github , so as i push the code to github repo my jenkins job triggerd and Failed at stage
scan image , Because i have used **trivy** to scan the image for Vulnerablities.
It is having **High and Critical** Vulnerablities so the CI stopped.



![Capture](https://user-images.githubusercontent.com/50741807/227479828-54f5b6bd-1958-45fe-8fd1-926e7c01d5c8.PNG)



**Console Output screenshot**



![Capture2](https://user-images.githubusercontent.com/50741807/227488676-7824bcfc-a49d-4aa3-91fa-dd84fd3fa239.PNG)


To remove these Vulnerablities we need to modify the Dockerfile, we can use distroless images or remove the unwanted packages from the base image.

To proceed furuther I have changed my jenkinsfile to just scan the Vulnerablities and proceed.



**Task3:**

For code quality/code coverage used SonarQube, Integrated sonarqube with the jenkins server .
In the Global tool configuration, configured the sonar scanner.
created the sonar-project.properties file.
Using build-in sonarway quality-gate.

![sonarQube](https://user-images.githubusercontent.com/50741807/227491758-ff567e32-d65d-45de-9e81-6deef27a463c.PNG)



**Task4:**

Build the Docker image in Ci, and push that to Docker hub and then deploy it into the Kubernets cluster.


![endtoend](https://user-images.githubusercontent.com/50741807/227494418-96f82af9-778d-428e-85a1-0f4780b1f263.PNG)



we can check that in k8 cluster

```bash
kubectl get deployment
```

![kubernetes](https://user-images.githubusercontent.com/50741807/227495259-187b279e-bd07-4e95-b7ca-9c09fddafcfb.PNG)



**Task5:**

Created the helm chart for the node app, used mongodb as dependency chart for that.
we can simply deploy this chart , with out configuring any mongodb server.

created the **argo-application.yaml** file , with help of this declarative file we can deploy the helm chart in kubernetes cluster using ArgoCd.

```bash
kubectl apply-f argo-application.yaml.

```

![Argocd](https://user-images.githubusercontent.com/50741807/227512750-a2fb42a8-b9fb-4a78-a022-64e09b1c4b46.PNG)



