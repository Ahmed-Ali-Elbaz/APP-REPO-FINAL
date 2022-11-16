
## Authors

- Ahmed Ali


## 🚀 About Me
I'm a DevOps Engineer...

# CICD Pipeline helloworld nodejs app using /Docker/Jenkins/Terraform/GKE with Slack Notification. (APP-REPO)


![image](https://drive.google.com/uc?export=view&id=1pPsHfDcJORYH6V9Mkl8g7VTuWtcjy-ZK)
## Demo

This Repo contains Pipeline section of the CICD Pipeline project I'm gonna explain CICD stages (fetch the code changes from github & build and push image to dockerhub & deploy hello world node.js app on GKE cluster & send notifications to slack channel).

Check infrastructure section in this Repo : https://github.com/Ahmed-Ali-Elbaz/APP-REPO-FINAL


## Tools & Plugins


#### Kubernetes :


  - Where we will deploy helloworld app on it.


#### Jenkins :


  - Create CICD pipeline to build and push the image of our helloworld app & deploy hello world app on GKE cluster & integrate our pipeline with Slack.


#### Slack Notification Plugin :
  - Send notifications to slack channel
## Pipeline
1- I will create a job Pipeline with name "helloWorldPipeline"
2- I will add github repo link and Jenkinsfile path and create github webhook to trigger our Pipeline 

![image](https://drive.google.com/uc?export=view&id=11i1wx1W3o5tlTkgKiVJZaa6HPBRUIJZh)

![image](https://drive.google.com/uc?export=view&id=1Nq6TQuJILRCe11eRdW7XLL8a9f2Pjn5f)

![image](https://drive.google.com/uc?export=view&id=1Wjky-_MyeMz5xyzREG0SuOG62wU0QRtG)



## Slack
1- I will create a channel with name "helloworldapp" and integrate it with Jenkins

![image](https://drive.google.com/uc?export=view&id=1ZlN7oxRVGIhvraeASbVgGXHUTeT4BlkG)



## helloworldapp docker file

1- I will create a docker file to create an image from hello world app (Jenkins will build and push this image to dockerhub)

![image](https://drive.google.com/uc?export=view&id=1PXIylDxBKhzkFVN-3qPRGgRkeq_sAyH-)


## Deployment files

- I will create 3 deployment files (app.yaml & service.yaml & prodns.yaml) Jenkins will deploy these files on GKE cluster

![image](https://drive.google.com/uc?export=view&id=1EvRWeop1S9Sv0S7yPU0UM-B9t9va0H0Y)

![image](https://drive.google.com/uc?export=view&id=1dkauO-iPWkvDX39EraN_lSiti9swX9Kz)

![image](https://drive.google.com/uc?export=view&id=1lYZzIQgIJDpWG20skXmkZEeZDCtcO6FT)


## Jenkinsfile

1- "CI" stage in the Pipeline will ( clone the github repo & build helloWorldapp image & push image to dockerhub ) "Pipeline will run on Jenkins Slave Pod"

![image](https://drive.google.com/uc?export=view&id=1AuAiGGQoVYy-YoCtOOphQoJ-FgRpz65k)

2- "CD" stage in the Pipeline will ( authenticate access to the cluster using Service account which is created with terraform in the infra section & gcloud auth command )
   I added a new credentials "secret file" in jenkins which contains Service account '.json key'

![image](https://drive.google.com/uc?export=view&id=18cp-nRc0sey3fRR_YJF4VIwQbtkCHFbf)

3- Slack Notifications this section will send Notifications to Slack channel in case ( SUCCEEDED | FAILD )

![image](https://drive.google.com/uc?export=view&id=1_NQ2U_cEODtJGnXm0uG6q8WtYXwBuHK-)





## Feedback

If you have any feedback, please reach out to me at ahmed.ali.elbaz.mohamed@gmail.com
